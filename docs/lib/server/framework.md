# Framework Module

The **Framework Module** acts as a bridge between Versa Library and the RP framework running on your server. Since each framework (QBCore, ESX, QBox, Ox, etc.) has its own unique player and character structures, this module provides a **centralized "character" object** that works the same way across all supported frameworks.

If you are using a custom framework, you can implement a **custom bridge** to connect it into Versa Library. Once integrated, your server scripts can interact with players through the same consistent `character` API, no matter which framework is underneath.

This makes it easier to:
- Write framework-agnostic scripts that work across multiple servers.
- Standardize how you access player data (money, inventory, jobs, etc.).
- Reduce code duplication and maintenance overhead.

## Import
If you want to import the framework module into any of your scripts, simply follow the code snippet below.
```lua
local framework = require '@versa_lib.modules.framework.server'
```

## Character Object
| Field       | Type    | Description                                 |
|------------|---------|---------------------------------------------|
| playerId   | string  | The unique citizen ID of the player (player id, state id, citizen id)|
| source     | number  | The player’s source ID in FiveM            |
| firstname  | string  | The player’s first name                     |
| lastname   | string  | The player’s last name                      |
| fullname   | string  | The player’s full name (firstname + lastname) |


## getPlayer
Get the character object from a source
```lua
local player = framework.getPlayer(source)
```
**Parameters**
- `source` (number) - The player’s source

**Returns**
- `character` (table | false) – The [character object](#character-object) if found, or false if no player exists with that source

## getPlayerFromId
Get the character object from the player’s unique identifier.
```lua
local player = framework.getPlayerFromId(playerId)
```
**Parameters**  
- `playerId` (string) – The player’s unique identifier (player id, state id, citizen id)

**Returns**  
- `character` (table | false) – The [character object](#character-object) if found, or `false` if no player exists with that identifier

## getPlayers
Get all active character objects.
```lua
local player = framework.getPlayers()
```
**Returns**  
- `characters` (table) – A table containing all currently active [character objects](#character-object)


## getMetaDataValue
Get a metadata key value pair on a character.
```lua
local value = framework.getMetaDataValue(source, key)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `key` (string) – The metadata key to retrieve

**Returns**  
- `value` (any) – The value of the requested metadata key for the [character object](#character-object), or `nil` if it does not exist

## setMetaDataValue
Set a metadata key value pair on a character.
```lua
local success = framework.setMetaDataValue(source, key, value)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `key` (string) – The metadata key to set  
- `value` (any) – The value to assign to the metadata key

**Returns**  
- `success` (boolean) – `true` if the value was successfully set, otherwise `false`

## addMoney
Add money to a character.
```lua
local success = framework.addMoney(source, type, amount, reason)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `type` (string) – The type of currency ("cash" or "bank")
- `amount` (number) – The amount of money to add  
- `reason` (string) – Reason for the transaction

**Returns**  
- `success` (boolean) – `true` if the money was successfully added, otherwise `false`

## removeMoney
Remove money from a character.
```lua
local success = framework.removeMoney(source, type, amount, reason)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `type` (string) – The type of currency (e.g., `"cash"`, `"bank"`)  
- `amount` (number) – The amount of money to remove  
- `reason` (string) – Reason for the transaction (optional for logs)

**Returns**  
- `success` (boolean) – `true` if the money was successfully removed, otherwise `false`