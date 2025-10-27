# Hooks Module

The **Hooking Module** provides a way to extend and control functionality within your codebase by registering hooks that run before certain actions are executed. Hooks allow developers to "intercept" logic, modify data, or prevent the default behavior from running altogether.

- **Register hooks anywhere** – you can attach custom logic to a specific hook type from any resource or script.
- **Shared execution** – all registered hooks for a given type will be executed when that hook is triggered.
- **Control flow** – if any hook returns `false`, the main hook action will be cancelled. This makes it easy to implement validation, permissions, or conditional checks.
- **Dynamic management** – hooks can be removed at runtime if no longer needed.

## Import
### Important Notice
* Hooks can be registered on both the client and the server. However, hooks registered on the client can only be listened to by the client, and hooks registered on the server can only be listened to by the server.
* For security and consistency, it’s strongly recommended to use server-side hooks whenever possible. Client-side hooks are provided as a convenience for local or non-sensitive use cases.

### Import Module
```lua
local Hook = require '@versa_sdk/modules/hooks'
```