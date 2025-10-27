# Chunk Module - Client
[Read Here](/sdk/chunks/import) on how to import the module into your scripts!

## GetEntityFromKey
Get local entity handle from chunk key
```lua  
local entity = Chunk.GetEntityFromKey(key)
```

**Example:**
```lua
local entity = Chunk.GetEntityFromKey(key)

-- With the entity handle we can then run natives like normal
SetEntityHeading(entity, 100)
```

**Parameters**
- `key` (string) - A unique identifier for the chunk entity

**Returns**
- `entity` (number | false) – Entity handle or false if no entity with that key is found