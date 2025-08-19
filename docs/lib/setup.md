# Versa Library - Setup

## **Requirements**
* [ox_lib](https://github.com/overextended/ox_lib) (Now maintained by [Community Ox](https://github.com/CommunityOx/ox_lib))
* [oxmysql](https://github.com/overextended/oxmysql) (Now maintained by [Community Ox](https://github.com/CommunityOx/oxmysql))

## **Configuration**
* You must setup everything in the config file to match the resources that you use. 
* If any of your resources you use are not supported, feel free to ask us to add it or add it your self by following our custom bridge tutorial below!

**Example Config**
```lua
return {
  Debug = false,

  Framework = 'qbox', -- esx, qb, qbox, ox
  Target = 'ox', -- ox, qb
  Inventory = 'ox', -- ox
}
```

## Custom Bridges
* Sometimes your resouces may not be supported by us out the box.
* Inside every bridge folder, we have included a folder called custom, with instructions on how to implement your system
* If you end up setting up a publicly available resource, feel free to make a [pull request](https://github.com/versa-development/versa_lib/pulls) so we can implement it for other people