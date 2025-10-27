# Notification Module - Server
[Read Here](/sdk/notification/import) on how to import the module into your scripts!

## Send
The notification function
```lua
Notification.Send(source, {
  title = 'Satisfied',
  message = 'Eaten burger!',
  duration = 5000,
  type = 'success', --info, success or error
})
```
**Parameters**  
- `source` (number) – The player’s server id
- `data` (table) - Notification Object