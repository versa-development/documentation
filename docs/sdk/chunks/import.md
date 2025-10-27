# Chunk Module

The **Chunk Module** divides the GTA world into manageable "chunks," similar to how games like Minecraft handle world loading. Objects, NPCs, and other entities are dynamically loaded or unloaded based on the chunk the player is currently in, improving performance for clients!

Key features include:
- **Dynamic loading** – only the objects and peds in the player’s current chunk (and surrounding chunks) are active.
- **Optimized performance** – reduces memory by unloading distant entities automatically.
- **Server-defined chunks** – all chunk data is managed server-side, preventing clients from dumping coordinates or discovering hidden locations.

## Import
```lua
local Chunk = require '@versa_sdk/modules/chunks'
```