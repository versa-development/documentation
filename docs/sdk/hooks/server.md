# Hooks Module - Server
[Read Here](/sdk/hooks/import) on how to import the hook module into your scripts!

## Trigger
Trigger a hook and run all registered listeners
```lua
-- This would be in the weed script. Inside the function to place a weed pot.
local success, error = Hook.Trigger('versa_weed:canPlacePot', {
    number = math.random(1, 3),
    string = 'hello',
    source = source
})
```
**Parameters**
- `hookName` (string) - The name of the hook to trigger
- `payload` (table) - Data passed to each listener

**Returns**
- `success` (boolean) - True if all listeners passed
- `error` (string|nil) - Error message if a listener blocked the hook

## Listen
Register a listener for a hook
```lua
-- This could be used anywhere (in this example, an apartment system)
local hookId = Hook.Listen('versa_weed:canPlacePot', function(payload)
    if isInApartment(payload.source) then
        return false, 'You cannot place a pot in your apartment.'
    end

    return true
end)
```
**Parameters**
- `hookName` (string) - The name of the hook to listen to
- `payload` (function) - The function to run when the hook is triggered; returning false will block execution

**Returns**
- `listenerId` (string) - Unique ID for this listener, used to delete it later


## Delete
Delete a registered hook listener by its ID given on the `Listen` function
```lua
local success = Hook.Delete(hookId)
```
**Parameters**
- `hookId` (string) - The listener ID returned from hook.on

**Returns**
- `success` (boolean) - True if the listener was successfully deleted, false otherwise