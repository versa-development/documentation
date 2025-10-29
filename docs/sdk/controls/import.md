# Controls Module

The **Controls Module** provides a simple interface for displaying dynamic on-screen keybind prompts (e.g., “E to Place” or “X to Cancel”) using GTA V’s native Instructional Buttons scaleform.

This module is designed to improve user feedback in interactive systems by clearly showing available controls at the bottom of the screen. It supports showing multiple keybindings at once and can be easily toggled on or off.

---
![Controls Example](/examples/controls.png)

## Import
* Please Note: The controls module cannot be imported onto the server
```lua
local Controls = require '@versa_sdk/modules/controls'
```