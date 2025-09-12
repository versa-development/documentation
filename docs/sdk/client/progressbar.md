# Progress Bar Module

The **Progress Bar** module acts as a bridge between the Versa SDK and the progress bar that you run on your server.  

## Import

```lua
local progress = require '@versa_sdk.modules.progress.client'
```

## init

Initialize an asynchronous progress bar.

```lua
local success = progress.init({
  label = 'Processing...',
  duration = 5000, -- 5 Seconds
  prop = { ... },
  animation = { ... },
  states = { ... }
})
```

**Returns**  
- `success` (boolean) – Whether the progress bar was completed  

**Parameters**

- `data` (table) – [Data Structure (Seen Below)](#data-structure)

## Data Structure
#### `label`

- Type: `string`  
- Description: The text displayed on the progress bar.

---

#### `duration`

- Type: `number`  
- Description: How long will the progress bar last? (milliseconds)

---

#### `prop`

- Type: `table` or `table[]`  
- Description: Props attached to the player during the progress. Can be a single prop table or an array of props. Each prop entry is a table with:

| Field      | Type       | Description                                     |
|------------|------------|-------------------------------------------------|
| `model`    | string     | The prop model name                              |
| `bone`     | number     | The GTA ped bone ID to attach the prop to       |
| `position` | vector3    | Offset from the bone (x, y, z)                  |
| `rotation` | vector3    | Rotation of the prop (x, y, z in degrees)       |

**Example — single prop:**

```lua
prop = {
  model = 'prop_tool_wrench',
  bone = 57005, -- Right Hand
  position = vector3(0.05, 0, 0),
  rotation = vector3(0, 0, 45),
}
```

**Example — two props:**

```lua
prop = {
  {
    model = 'prop_tool_box_04',
    bone = 18905, -- Left Hand
    position = vector3(0.05, 0, 0),
    rotation = vector3(0, 90, 0),
  },
  {
    model = 'prop_tool_wrench',
    bone = 57005, -- Right Hand
    position = vector3(0, 0.05, 0),
    rotation = vector3(0, 0, 45),
  }
}
```

---

#### `animation`

- Type: `table`  
- Description: Animation to play during the progress bar. Fields:  

| Field    | Type    | Description                           |
|----------|--------|---------------------------------------|
| `dict`   | string | Animation dictionary                   |
| `name`   | string | Animation name                          |
| `flags`  | number | Animation flags (loop, upper body, etc.) |

---

#### `states`

- Type: `table`  
- Description: Controls player behavior during the progress. Fields:

| Field                  | Type    | Description                         |
|------------------------|---------|-------------------------------------|
| `useWhileDead`         | boolean | Can progress bar be used while dead |
| `canCancel`            | boolean | Whether player can cancel            |
| `disableMovement`      | boolean | Disable movement while in progress  |
| `disableDriving`       | boolean | Disable driving                      |
| `disableCombat`        | boolean | Disable combat                       |
| `disableMouseMovement` | boolean | Disable camera/mouse movement        |
| `disableSprint`        | boolean | Disable sprinting                    |

## Example
This is an example with using two props (one in the left hand, one in the right hand)

```lua
RegisterCommand('sdk:progress', function()
  local success = progress.init({
    label = 'Processing...',
    duration = 5000, -- 5 Seconds
    prop = { 
      {
        model = 'prop_tool_box_04',
        bone = 18905, -- Left Hand
        position = vector3(0.05, 0, 0), 
        rotation = vector3(0, 270, 0),
      },
      {
        model = 'prop_tool_wrench',
        bone = 57005, -- Right Hand
        position = vector3(0.05, 0, 0),
        rotation = vector3(0.05, 0, 45),
      }
    },
    animation = {
      dict = 'amb@world_human_welding@male@base',
      name = 'base',
      flags = 16,
    },
    states = {
      useWhileDead = false,
      canCancel = true,
      disableMovement = false,
      disableDriving = true,
      disableCombat = true,
      disableMouseMovement = false,
      disableSprint = true,
    }
  })

  print('Progress Bar Result:', success)
end)
```