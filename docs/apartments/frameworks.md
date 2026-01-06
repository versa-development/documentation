# Framework Setups:
All frameworks are different, and some need extra changes sometimes! These changes can be hard for people with little to no experience with coding, feel free to open a ticket on our Discord if you need support!

## Spawn Selector Conflicts 
If you have a spawn selector system & have `Config.TeleportToApartmentOnCreate` set to true, you may have conflicting issues.
* To fix any conflicting issues: you can disable `TeleportToApartmentOnCreate` in the config file and:
  * Use the server export `exports.versa_apartments:TeleportToApartment(source)` on your spawn selector

## Assigning / Unassigning Rooms
* Within the [Versa SDK](/sdk/intro), all [frameworks have events setup](/sdk/framework/events) for when a player joins/leaves.
* The apartment system listens to these events (versa_apartments/server/events.lua - file is open-source) and assigns a room / unasssigns a room with the events.
* You can change when rooms are assigned & unassigned in that file.

## Qbox
*No Framework Specific Installation Required*

## ESX
*Not yet tested*

## QBCore
*Not yet tested*

## Custom/Unsupported
Everything is pretty simple to use and port over. However, if the Versa SDK does not support your framework there's a bit of a setup. Feel free to open a ticket and we will happily help support your framework!