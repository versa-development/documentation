# Framework Module - Objects

## Player Object
| Field       | Type    | Description |
|-------------|---------|-----------------------------------------------------------------------------|
| identifier  | string  | The unique identifier of the player (citizenid, identifier, state id, etc.) |
| source      | number  | The player's source |
| name        | table   | The character’s name data |
| ├─ first    | string  | The character’s first name |
| ├─ last     | string  | The character’s last name |
| └─ full     | string  | The character’s full name (first + last) |
| metadata    | table   | The character's meta data (key : value) |