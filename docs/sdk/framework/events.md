# Framework Module - Objects
Every framework setup has an "on player load" and an "on player unload" event to the server & the client for centralisation for Versa scripts.

## Setup
* If using a custom framework, you will need to setup these events. Follow the other framework setups in the file!

## playerLoaded
### Server:
::: warning
It is important you use AddEventHandler on the server for secruity reasons.
:::
```lua
AddEventHandler('versa_sdk:framework:playerLoaded', function(source)
    print('player ' .. source .. 'has loaded in')
end)
```

### Client:
```lua
RegisterNetEvent('versa_sdk:framework:playerLoaded', function()
    print('I have loaded in yay')
end)
```

## playerUnloaded
### Server:
::: warning
It is important you use AddEventHandler on the server for secruity reasons.
:::
```lua
AddEventHandler('versa_sdk:framework:playerUnloaded', function(source)
    print('player ' .. source .. 'has left or changed character')
end)
```

### Client:
```lua
RegisterNetEvent('versa_sdk:framework:playerUnloaded', function()
    print('I have unloaded')
end)
```