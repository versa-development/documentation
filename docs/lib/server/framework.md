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

## getPlayer
Get the character object from a source
```lua
local player = framework.getPlayer(source)
```
* @source: `number`
* @return: `table` | `boolean` 

## getPlayerFromId
Get the character object from the character unqiue identifier
```lua
local player = framework.getPlayerFromId(identifier)
```
* @identifier `number`
* @return `table` | `boolean`

## getPlayers
Get all active chatracter objects

## getMetaDataValue
Get a metadata key value pair on a character

## setMetaDataValue
Set a metadata key value pair on a character

## addMoney
Add money to a character

## removeMoney
Remove money from a character