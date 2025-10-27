# Inventory Module - Server
[Read Here](/sdk/inventory/import) on how to import the module into your scripts!

## GiveItem
Gives an item to a player
```lua
local success = Inventory.GiveItem(source, item, amount, metadata)
```
**Parameters**
- `source` (number) - The player’s source
- `item` (string) - The name of the item
- `amount` (number) - The amount of items to give
- `metadata` (table) (optional) - Whether the item(s) should have metadata

**Returns**
- `success` (boolean) – Whether it was successful giving the item

## RemoveItem
Removes the item from a player
```lua
local success = Inventory.RemoveItem(source, item, amount, metadata, slot)
```
**Parameters**
- `source` (number) - The player’s source
- `item` (string) - The name of the item
- `amount` (number) - The amount of items to give
- `metadata` (table) (optional) - Only remove item with exact metadata
- `slot` (number) (optional) - Only remove item from an exact slot

**Returns**
- `success` (boolean) – Whether it was successful removing the item

## HasItem
Checks if the player has an item and returns the count
```lua
local hasItem, count = Inventory.HasItem(source, item, metadata)
```
**Parameters**
- `source` (number) - The player’s source
- `item` (string) - The name of the item
- `metadata` (table) (optional) - Only checks item with specific metadata

**Returns**
- `hasItem` (boolean) – Whether the player has the item or not
- `count` (number) - How many of the item the player has
