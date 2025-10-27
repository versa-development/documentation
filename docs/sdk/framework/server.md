# Framework Module - Server
[Read Here](/sdk/framework/import) on how to import the module into your scripts!

## GetPlayer
Get the character object from a source
```lua
local player = Framework.GetPlayer(source)
```
**Parameters**
- `source` (number) - The player’s source

**Returns**
- `character` (table | false) – The [character object](/sdk/framework/objects#character-object) if found, or false if no player exists with that source

## GetPlayerFromIdentifier
Get the character object from the player’s unique identifier.
```lua
local player = Framework.GetPlayerFromIdentifier(identifier)
```
**Parameters**  
- `identifier` (string) – The player’s unique identifier (player id, state id, citizen id)

**Returns**  
- `character` (table | false) – The [character object](/sdk/framework/objects#character-object) if found, or `false` if no player exists with that identifier

## GetPlayers
Get all active character objects.
```lua
local players = Framework.GetPlayers()
```
**Returns**  
- `characters` (table) – A table containing all currently active [character object](/sdk/framework/objects#character-object)


## GetMetaDataValue
Get a metadata key value pair on a character.
```lua
local value = Framework.GetMetaDataValue(source, key)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `key` (string) – The metadata key to retrieve

**Returns**  
- `value` (any) – The value of the requested metadata key for the [character object](/sdk/framework/objects#character-object), or `nil` if it does not exist

## SetMetaDataValue
Set a metadata key value pair on a character.
```lua
local success = Framework.SetMetaDataValue(source, key, value)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `key` (string) – The metadata key to set  
- `value` (any) – The value to assign to the metadata key

**Returns**  
- `success` (boolean) – `true` if the value was successfully set, otherwise `false`

## AddMoney
Add money to a character.
```lua
local success = Framework.AddMoney(source, type, amount, reason)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `type` (string) – The type of currency ("cash" or "bank")
- `amount` (number) – The amount of money to add  
- `reason` (string) – Reason for the transaction

**Returns**  
- `success` (boolean) – `true` if the money was successfully added, otherwise `false`

## RemoveMoney
Remove money from a character.
```lua
local success = Framework.RemoveMoney(source, type, amount, reason)
```
**Parameters**  
- `source` (number) – The player’s source ID  
- `type` (string) – The type of currency (e.g., `"cash"`, `"bank"`)  
- `amount` (number) – The amount of money to remove  
- `reason` (string) – Reason for the transaction (optional for logs)

**Returns**  
- `success` (boolean) – `true` if the money was successfully removed, otherwise `false`