# Hooking Module

The **Hooking Module** provides a way to extend and control functionality within your codebase by registering hooks that run before certain actions are executed. Hooks allow developers to "intercept" logic, modify data, or prevent the default behavior from running altogether.

- **Register hooks anywhere** – you can attach custom logic to a specific hook type from any resource or script.
- **Shared execution** – all registered hooks for a given type will be executed when that hook is triggered.
- **Control flow** – if any hook returns `false`, the main hook action will be cancelled. This makes it easy to implement validation, permissions, or conditional checks.
- **Dynamic management** – hooks can be removed at runtime if no longer needed.

## Import
If you want to import the hook module into any of your scripts, simply follow the code snippet below.
```lua
local hook = require '@versa_lib.modules.hooks.server'
```

## trigger
Trigger a hook and run all registered listeners
```lua
-- This would be in the weed script. Inside the function to place a weed pot.
local success, error = hook.trigger('versa_weed:canPlacePot', {
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

## on
Register a listener for a hook
```lua
-- This could be used anywhere (in this example, an apartment system)
local hookId = hook.on('versa_weed:canPlacePot', function(payload)
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


## delete
Delete a registered hook listener by its ID given on the `triggerHook` and `on` functions
```lua
local success = hook.delete(hookId)
```
**Parameters**
- `hookId` (string) - The listener ID returned from hook.on

**Returns**
- `success` (boolean) - True if the listener was successfully deleted, false otherwise