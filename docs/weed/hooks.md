# Versa Weed - Hooks
We provide hooks within the resource so you can easily add your own validation without needing direct access to the code!

* 📖 [Hooks Documentaion](/sdk/hooks/import)

## Server
### Place Pot
```lua
Hook.Listen('versa_weed:canPlacePot', function(payload)
    local source = payload.source -- number
    local potCoords = payload.coords -- vector4

    return true
end)
```

### Place Bagging Table
```lua
Hook.Listen('versa_weed:canPlaceBaggingTable', function(payload)
    local source = payload.source -- number
    local tableCoords = payload.coords -- vector4

    return true
end)
```

## Example
This example stops people from placing pots in an apartment.
* For this example, this code is placed in a hypothetical apartment system with a `IsInApartment` functions which returns a boolean whether a player is in an apartment

```lua
Hook.Listen('versa_weed:canPlacePot', function(payload)
    local source = payload.source -- number
    local potCoords = payload.coords -- vector4

    -- Do not allow people to place pots while in an apartment
    if IsInApartment(source) then
        TriggerClientEvent('notification', source, 'You cannot place pots in your apartment')
        return false, 'Cannot place pots in your apartment'
    end

    -- If not in an apartment, send true 
    return true
end)
```