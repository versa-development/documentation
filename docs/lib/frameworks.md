# Versa Library - Frameworks
The framework bridge is the middleware between the library and the framework you use on your server. Frameworks such as QBCore, ESX, QBox and Ox come out the box. If you have a custom framework follow the custom bridge setup. 

## Import
If you want to import the framework module into any of your scripts, simply follow the code snippet below.
```lua
local framework = require '@versa_lib.modules.framework.server'
```

### getPlayer
Get the character object from a source
```lua
local player = framework.getPlayer(source)
```
* @source: `number`
* @return: `table` or `boolean` 
