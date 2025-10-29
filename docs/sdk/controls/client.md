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

---

![Controls Multiple Example](/examples/controls_multiple.png)

```lua
Controls.Show({
    { control = {'A', 'D'}, text = 'Rotate Bag' },
    { control = 'X', text = 'Cancel' },
})
```
**Parameters**
- `data` (string[]) - Table of strings with the `control` and `text` property
  - `control` (string or string[]) - The control type
  - `text` (string) - Text to display next to the keybind

## Hide
Hide the controls menu
```lua
Controls.Hide()
```