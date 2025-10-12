# Chunk Module

The **Chunk Module** divides the GTA world into manageable "chunks," similar to how games like Minecraft handle world loading. Objects, NPCs, and other entities are dynamically loaded or unloaded based on the chunk the player is currently in, improving performance and reducing server load.

Key features include:
- **Dynamic loading** – only the objects and peds in the player’s current chunk (and nearby chunks) are active.
- **Optimized performance** – reduces memory and CPU usage by unloading distant entities automatically.
- **Server-defined chunks** – all chunk data is managed server-side, preventing clients from dumping coordinates or discovering hidden locations.

## Import
If you want to import the chunk module into any of your scripts, simply follow the code snippet below.
```lua
local chunk = require '@versa_sdk/modules/framework/chunks'
```

## create
Create a chunk entity.
```lua  
local success, error = chunk.create(type, key, data)
```

**Example:**
```lua
local success, error = chunk.create('object', 'versa_weed_pot_1', {
    model = 'empty_pot',
    coords = vector4(0, 0, 0, 180),
    target = {
      title = 'Inspect Pot',
      icon = 'fas fa-seedling',
      distance = 3.0,
      event = {
        type = 'client',
        name = 'versa_weed:client:inspectPot',
        parameters = { data.id }
      }
    }
})
```
* **The model and coords properties are the only required properties. You do not need to send through target data when creating a chunk entity.**
* **The target connects to the target module setup in the SDK**  

**Parameters**
- `type` (string) - Either object or ped
- `key` (string) - A unique identifier for the chunk entity
- `data` (table) - Chunk Object

**Returns**
- `success` (boolean) – Whether the chunk entity was created successfully
- `error` (string | false) – If not successful, this returns an error why the operation failed.

## edit
Edit a chunk entity
```lua  
local success, error = chunk.edit(key, data)
```

**Example (Swapping Model & Moving Object):**
```lua
chunk.edit('versa_weed_pot_1', { 
    model = 'full_pot',
    coords = vector4(1, 1, 1, 180) -- Not needed if you only want to swap the model
})
```

**Example (Removing the target):**
```lua
chunk.edit('versa_weed_pot_1', { 
    target = false -- You could also define a new target here
})
```

**Parameters**
- `key` (string) - A unique identifier for the chunk entity
- `data` (table) - Chunk Object

**Returns**
- `success` (boolean) – Whether the chunk entity was edited successfully
- `error` (string | false) – If not successful, this returns an error why the operation failed.

## delete
Delete a chunk entity.
```lua  
local success, error = chunk.delete(key)
```

**Parameters**
- `key` (string) - A unique identifier for the chunk entity

**Returns**
- `success` (boolean) – Whether the chunk entity was created successfully
- `error` (string | false) – If not successful, this returns an error why the operation failed.