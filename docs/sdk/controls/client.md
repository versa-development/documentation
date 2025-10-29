# Controls Module - Client
[Read Here](/sdk/controls/import) on how to import the hook module into your scripts!

## Show
Show the controls menu

![Controls Example](/examples/controls.png)

```lua
Controls.Show({
    { control = 'E', text = 'Place' },
    { control = 'X', text = 'Cancel' },
})
```
**Parameters**
- `data` (string[]) - Table of strings with the `control` and `text` property

## Hide
Hide the controls menu
```lua
Controls.Hide()
```