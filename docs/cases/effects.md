# Versa Cases - Effects
The script features a highly optimized effects system that allows you to create limitless, cinematic unboxing experiences for your players.

Whether you want a simple UI click with a flash of light, shoots 20 fireworks into the sky or throw confetti around you can do it all right from the config.

## How It Works
Every preset in `Config.CaseFxPreSets` is broken down into two main categories:
* `staticEffects` These run continuously from the moment the case opens until it completely closes (e.g. ambient glowing lights).
* `timedEffects` These trigger at exact millisecond intervals. Use `time = 0` for effects when the case first opens, or match time to your spinDuration (e.g., 5000) so the effect fires exactly when the winning item lands! (e.g. a firework)

Example Structure:
```lua
myCustomCase = {
    duration = 10000,     -- Total time the case is open (ms)
    spinDuration = 5000,  -- When the item finally lands (ms)
    
    staticEffects = { ... },
    timedEffects = { ... }
}
```

## Supported Effect Types
You can mix and match these effect types endlessly.

### 1. Light (type = 'light')
Creates a 3D ambient light source at the case. Mostly used in `staticEffects`.

**Paramaters:**
* `offset` (vector3) Position relative to the case.
* `color` ({r, g, b}) An RGB colour code for the light
* `distance` (number) How far the light travels.
* `brightness`: (number) Intensity of the light.

**Example:**
> This is an example of a pink light looking down at the case as a static effect.
```lua
{ 
    type = 'light',
    offset = vector3(0.0, 0.0, 1.0),
    color = { r = 255, g = 10, b = 200 },
    distance = 8.0,
    brightness = 3.0 
}
```

### 2. Particle (type = 'particle')
Spawns GTA V particle FX. (Static effects will loop automatically & timed effects will play once).

**Paramaters:**
* `dict` (string) The particle dictionary (e.g., 'core'). 
* `name` (string) The particle name (e.g., 'ent_dst_elec_fire_sp').
  * ([View all particle types here](https://wiki.rage.mp/wiki/Particles_Effects)). 
* `offset` (vector3) Position relative to the case.
* `scale` (number) Size multiplier of the particle.
* `color` (Optional) {r, g, b} Tints the particle (Great for fireworks!).

**Example:**
> This is an example of x3 confetti particles bursting out every 200 ticks (3 times in 0.8 seconds) 
```lua
{ 
    time = 5000, -- Happens 5 seconds after opening case 
    type = 'particle', 
    dict = 'scr_xs_celebration', 
    name = 'scr_xs_confetti_burst', 
    offset = vector3(0.0, 0.0, 0.5), 
    scale = 1.5, 
    count = 3, -- Run this 3 times
    interval = 200 -- Every 200ms (0.2 seconds)
},
```

### 3. Sound (type = 'sound')
Plays 3D spatial audio originating from the case.

**Paramaters:**
* `audioName` (string) Name of the sound. 
* `audioRef` (string) The audio reference set.
* `audioBank` (Optional) If using a specific DLC sound that requires a bank to be loaded.
  * ([View all sound types here](https://wiki.rage.mp/wiki/Sounds))

**Example:**
> This is an example of the Property Purchase Sound effect playing 5 seconds after the case being opened
```lua
{ 
    time = 5000, -- Play 5 seconds after the case opens
    type = 'sound',
    audioName = 'PROPERTY_PURCHASE',
    audioRef = 'HUD_AWARDS' 
},
```

### 4. Explosion (type = 'explosion')
Creates a visual explosion. Note: Damage is forced to 0.0 in the engine, so it will never kill players.

**Paramaters:**
* `expType` (number) The GTA V explosion type ID. 
  * ([View all explosion types here](https://wiki.rage.mp/wiki/Explosions))
* `scale` (number) Size of the explosion.

**Example:**
> This is an example of an explosion
```lua
{ 
    type = 'explosion',
    expType = 69,
    offset = vector3(0.0, 0.0, 1.0),
    scale = 0.5 
}
```

### 5. Screen Shake (type = 'screenshake')
Rumbles the player's camera.

**Paramaters:**
* `shakeName` (string) Type of shake (e.g., 'HAND_SHAKE', 'LARGE_EXPLOSION_SHAKE').
  * ([View all shake types here](https://wiki.rage.mp/wiki/Cam::shakeCinematic))
* `intensity` (number) Multiplier for the shake force.

**Example:**
> This is an example of a slight screen shake
```lua
{ 
    type = 'screenshake',
    shakeName = 'LARGE_EXPLOSION_SHAKE',
    intensity = 0.6 
}
```

### 6. Timecycle Filter (type = 'timecycle')
Applies a visual screen filter to the player

**Paramaters:**
* `filterName` (string) Name of the GTA timecycle modifier. ([View all timecycle filters here](https://wiki.rage.mp/wiki/Timecycle_Modifiers)). 
* `duration` (number) How long (in ms) the timecycle lasts for

**Example:**
> This is an example of the specator5 timecycle modifier
```lua
{ 
    time = 5000, -- Starts after 5000ms (5 seconds)
    type = 'timecycle',
    filterName = 'spectator5',
    duration = 3000 
}
```

## Repeater System
Want to shoot a barrage of fireworks? Instead of writing 20 lines of config, you can use the built-in Repeater logic on any timed effect. 

**Example:**
> Adding `count` and `interval` to the array allows you to repeat effects.
```lua
{ 
    time = 5000, 
    type = 'particle', 
    dict = 'scr_indep_fireworks', 
    name = 'scr_indep_firework_starburst', 
    offset = vector3(0.0, 0.0, 2.0), 
    scale = 1.0, 
    color = { r = 255, g = 0, b = 0 },
    count = 10,      -- Will fire 10 times in a row
    interval = 100   -- Waits 100ms between each shot
                     -- In total, 10 fireworks will shoot every 0.1 seconds
}
```

## Adding Your Own Custom Logic
* The effects file (`client/cl_effects.lua`) is open-source so you can add your own effects!
* Want an effect that spawns an aggressive dog when a player gets a bad item? Or maybe an effect that gives the player a temporary speed boost?

**Example:**
* Open cl_effects.lua.
* Find the `executeTimedEffect(fx)` function.
* Add a new `elseif`

```lua
elseif fx.type == 'spawn_ped' then
    -- Your custom logic here!
    -- Use fx.pedModel, fx.offset, etc.
end
```

Now you can use `{ type = 'spawn_ped', pedModel = 'a_c_chop' }` right in your config!