# Versa Library - Frameworks
The framework bridge is the middleware between the library and the framework you use on your server. Frameworks such as QBCore, ESX, QBox and Ox come out the box. If you have a custom framework follow the custom bridge setup. 

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