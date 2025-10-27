# Framework Module

The **Framework Module** acts as a bridge between the Versa SDK and the RP framework running on your server. Since each framework (QBCore, ESX, QBox, Ox, etc.) has its own unique player and character structures, this module provides a **centralized "character" object** that works the same way across all supported frameworks.

If you are using a custom framework, you can implement a **custom bridge** to connect it into the Versa SDK. Once integrated, your server scripts can interact with players through the same consistent `character` API, no matter which framework is underneath.

This makes it easier to:
- Write framework-agnostic scripts that work across multiple servers.
- Standardize how you access player data (money, inventory, jobs, etc.).
- Reduce code duplication and maintenance overhead.

## Import
* Please Note: The framework module cannot be imported onto the client
```lua
local Framework = require '@versa_sdk/modules/framework'
```