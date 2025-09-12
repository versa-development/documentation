# Inventory Module

The **Inventory Module** provides a unified interface for managing player inventories across different FiveM frameworks and inventory systems. Since each framework often handles inventories in its own way, this module standardizes common inventory operations such as adding, removing, and checking items.

## Import
If you want to import the ivnentory module into any of your scripts, simply follow the code snippet below.
```lua
local inventory = require '@versa_sdk.modules.inventory.server'
```

## giveItem
Gives an item to a player
```lua
local success = inventory.giveItem(source, item, amount, metadata)
```
**Parameters**
- `source` (number) - The player’s source
- `item` (string) - The name of the item
- `amount` (number) - The amount of items to give
- `metadata` (table) (optional) - Whether the item(s) should have metadata

**Returns**
- `success` (boolean) – Whether it was successful giving the item

## removeItem
Get the character object from a source
```lua
local success = inventory.removeItem(source, item, amount, metadata, slot)
```
**Parameters**
- `source` (number) - The player’s source
- `item` (string) - The name of the item
- `amount` (number) - The amount of items to give
- `metadata` (table) (optional) - Only remove item with exact metadata
- `slot` (number) (optional) - Only remove item from an exact slot

**Returns**
- `success` (boolean) – Whether it was successful removing the item

## hasItem
Get the character object from a source
```lua
local hasItem, count = inventory.hasItem(source, item, metadata)
```
**Parameters**
- `source` (number) - The player’s source
- `item` (string) - The name of the item
- `metadata` (table) (optional) - Only checks item with specific metadata

**Returns**
- `hasItem` (boolean) – Whether the player has the item or not
- `count` (number) - How many of the item the player has
