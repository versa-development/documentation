# Notification Module

The **Notification** module acts as a bridge between the Versa SDK and the progress bar that you run on your server.  

## Import
```lua
local notification = require '@versa_sdk.modules.notification.client'
```

## notify
The notification function
```lua
notification.notify({
  title = 'Satisfied',
  message = 'Eaten burger!',
  duration = 5000,
  type = 'success', --info, success or error
})
```