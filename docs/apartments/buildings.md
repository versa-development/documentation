# Supported MLOs
### OFFERING DISCOUNTS FOR PEOPLE HELPING:
If your MLO is not supported & is a public resource (free or paid) and you're willing to build the config for the building, we will offer a discount on the resource! Create a ticket on our Discord

## MLO not supported?
No worries, the apartment system comes with a generic config file to help get you started! Follow the example below, or make a ticket in the Discord to help get started!
```lua
-- config/locations/example.lua
return {
    label = 'Example Apartments', -- The name of the apartment building
    lobbyCoords = vector4(-773.7421, 306.7979, 85.7000, 0.0642), -- The coordinates of the apartment building lobby
    lobbyPedCoords = vector4(-773.7421, 305.7979, 84.7000, 0.0642), -- The coordinates where the apartment lobby ped will spawn
    rooms = {
        {
            label = 'Room 1',
            coords = vector4(-773.7421, 306.7979, 85.7000, 0.0642),
            outfits = vector4(-773.7421, 306.7979, 85.7000, 0.0642),
            stash = vector4(-773.7421, 306.7979, 85.7000, 0.0642),
            --doorName = 'example_room_1' -- ox_doorlock door name- if not used here the name will be: <building_key(filename)>_<index> (This room would be example_1)
            --ipls = {'some_ipl', 'another_ipl'} -- Optional incase this room is on a floor that needs IPLs loaded (you are responsible for unloading them when no longer needed)
        }
    }
}
```

## kiiya
* Lapureta Apartments
  * [📺 Preview](https://www.youtube.com/watch?v=WbhePrZBcdI)
  * Config Setup:
    * `config/sv_config.lua` -> `Config.Apartments = { 'kiiya_lapureta' }`
