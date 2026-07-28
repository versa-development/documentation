# Versa Cases - Hooks
We provide hooks within the resource so you can easily add your own validation without needing direct access to the code!

* 📖 [Hooks Documentaion](/sdk/hooks/import)

## Server
### Place Case
```lua
Hook.Listen('versa_cases:canPlaceCase', function(payload)
    local source = payload.source -- number
    local caseType = payload.caseType -- string
    local caseCoords = payload.coords -- vector4

    return true
end)
```

### Use Preplaced Case
```lua
Hook.Listen('versa_weed:canUsePrePlacedCase', function(payload)
    local source = payload.source -- number
    local caseType = payload.caseType -- string
    local caseCoords = payload.coords -- vector4

    return true
end)
```