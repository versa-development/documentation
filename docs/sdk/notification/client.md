# Notification Module - Client
[Read Here](/sdk/notification/import) on how to import the module into your scripts!

## Send
The notification function
```lua
Notification.Send({
  title = 'Satisfied',
  message = 'Eaten burger!',
  duration = 5000,
  type = 'success', --info, success or error
})
```
**Parameters**  
- `data` (table) - Notification Object