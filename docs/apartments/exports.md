# Versa Apartments - Exports

## Server
### LoadPlayerApartment
Load a room for a player (built-in already)
* Built in `versa_apartments/server/events.lua` (File is open)
```lua
exports.versa_apartments:LoadPlayerApartment(source)
```

### UnloadPlayerApartment
Unload a player's room (built-in already)
* Built in `versa_apartments/server/events.lua` (File is open)
```lua
exports.versa_apartments:UnloadPlayerApartment(source)
```

### GetPlayerApartment
Get the apartment of a player
```lua
local apartment = exports.versa_apartments:GetPlayerApartment(source)
```

### TeleportToApartment
Teleport a player into their apartment room.
* This export uses the coordinate setup in a room config : `coords` 
```lua
exports.versa_apartments:TeleportToApartment(source)
```