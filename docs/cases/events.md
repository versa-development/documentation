# Versa Cases - Events
We provide base events we feel are needed for your own use. Please open a ticket on our Discord if you need another event for your own needs!

## Client
### `versa_cases:client:beginPlacing`
* This event triggers the placing of a case. This would typically be attached to an item.
* Please Note: This event does not validate whether the player has the required item and/or key. However, when the player presses E to place, the server validates whether the player has the required item(s)

**Paramaters:**
* `caseType` - The key of the case defined in the config file (Config.Cases)

```lua
-- CLIENT
TriggerEvent('versa_cases:client:beginPlacing', caseType)

-- SERVER
TriggerClientEvent('versa_cases:client:beginPlacing', source, caseType)
```

## Server
### `versa_cases:server:caseOpened`
* This event is broadcast to the server once someone has opened a case and has been given their reward.

**Paramaters:**
* `source` - The online player id
* `caseType` - The key of the case defined in the config file (Config.Cases)
* `caseCoords` - The coordinates of the case (not the player)
* `reward` - An array of the reward they were given (The array from the Config.Cases[...].rewards)

::: danger
NEVER register this event using RegisterNetEvent. This event is server-side only and must only be handled using AddEventHandler. A malicious actor can potentially trigger the event themselves and spoof a case opening
:::
```lua
-- GOOD SECURITY: DO NOT USE RegisterNetEvent or RegisterServerEvent
AddEventHandler('versa_cases:server:caseOpened', function(source, caseType, caseCoords, reward)
    local source = source
    local caseType = caseType
    local caseCoords = vector4(caseCoords.x, caseCoords.y, caseCoords.z, caseCoords.w)
    local reward = {
        label = reward.label,
        itemName = reward.itemName,
        itemAmount = reward.itemAmount,
        chance = reward.chance,
        color = reward.color,
        image = reward.image
    }

    print(source .. ' has opened a case and won x' .. reward.itemAmount .. ' ' .. reward.label)
end)
```