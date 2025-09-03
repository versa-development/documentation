# Hooking Module

The **Hooking Module** provides a way to extend and control functionality within your codebase by registering hooks that run before certain actions are executed. Hooks allow developers to "intercept" logic, modify data, or prevent the default behavior from running altogether.

- **Register hooks anywhere** – you can attach custom logic to a specific hook type from any resource or script.
- **Shared execution** – all registered hooks for a given type will be executed when that hook is triggered.
- **Control flow** – if any hook returns `false`, the main hook action will be cancelled. This makes it easy to implement validation, permissions, or conditional checks.
- **Dynamic management** – hooks can be removed at runtime if no longer needed.

### Example

```lua
-- Banking Script
local hook = require '@versa_lib.modules.server.hooks'

RegisterNetEvent('banking:makePayment', function(data)
    -- Trigger all hooks before running the main logic
    local success, error = hook.registerHook('makeBankPayment', source, data)

    if success then
        makePayment(data)
    else
        notification(source, error or "Payment blocked by a hook")
    end
end)

-- 3rd Party Script
local hook = require '@versa_lib.modules.server.hooks'

-- Register a hook to intercept bank payments
local hookId = hook.on('makeBankPayment', function(source, data)
    -- Example: block players without the correct state
    if playerState[source] then
        return true
    end

    return false, "You are not allowed to make payments right now."
end)

-- Command to remove the hook at runtime
RegisterCommand('deletehook', function()
    hook.delete(hookId)
    print("makeBankPayment hook deleted")
end)