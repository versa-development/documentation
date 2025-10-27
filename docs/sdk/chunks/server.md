# Chunk Module - Server
[Read Here](/sdk/chunks/import) on how to import the module into your scripts!

## Create
Create a chunk entity.
```lua  
local success, error = Chunk.Create(type, key, data)
```

**Example:**
```lua
local success, error = Chunk.Create('object', 'versa_weed_pot_1', {
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

## Edit
Edit a chunk entity
```lua  
local success, error = Chunk.Edit(key, data)
```

**Example (Swapping Model & Moving Object):**
```lua
Chunk.Edit('versa_weed_pot_1', { 
    model = 'full_pot',
    coords = vector4(1, 1, 1, 180) -- Not needed if you only want to swap the model
})
```

**Example (Removing the target):**
```lua
Chunk.Edit('versa_weed_pot_1', { 
    target = false -- You could also define a new target here
})
```

**Parameters**
- `key` (string) - A unique identifier for the chunk entity
- `data` (table) - Chunk Object

**Returns**
- `success` (boolean) – Whether the chunk entity was edited successfully
- `error` (string | false) – If not successful, this returns an error why the operation failed.

## Delete
Delete a chunk entity.
```lua  
local success, error = Chunk.Delete(key)
```

**Parameters**
- `key` (string) - A unique identifier for the chunk entity

**Returns**
- `success` (boolean) – Whether the chunk entity was created successfully
- `error` (string | false) – If not successful, this returns an error why the operation failed.