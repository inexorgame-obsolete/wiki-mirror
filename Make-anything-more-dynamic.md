Sauerbraten is more or less a very static game. In future, we should reduce the core functionalities to a minimum but make things extendable. There are lots of possibilities which would increase the fun dramatically.

## Dynamicification Possibilities

* [New dynamic entity system](Entity System)
* [New dynamic particle system](Particle System)
* Unlimited types of weapons
* Unlimited types of player models
* Dependency management/ingame downloader for content
* Unlimited, scriptable types of game modes
* New dynamic 2D effect system
 * [Destructible map geometry](https://www.youtube.com/watch?v=VPdKX7UhneY&index=2&list=PLCbZc-GgCGzLhkGS5l850tjCQrPUeapK6)
* Location based effects
* Customizable HUD
* Movable objects (in multiplayer) 

### Unlimited types of weapons

* API for the weapon game logic
 * reloading
 * shot
 * hud updates
 * bouncer control
* 3D Model Files
 * 1st Person
 * 3rd Person

### Unlimited types of player models

Currently there is a fixed number of player models. To make it more dynamic it would require to address player models by name instead of a number.

* Player-Model Configuration (Name, Description)
* 3D Model Files
* Preview

### Dependency management for content

Content depends on other content. The goal is to reduce redundancy which makes the game more lightweight and faster: less hard drive space needed, decreased download duration and increased map loading times. Nowadays we can't deliver one single package anymore: it would be too big and we would dictate what content the player have to play. Instead the game should dynamically update the content dependent on the players needs. There's no need to deliver 80 ctf maps if the player only plays regen capture for example.

#### Dependencies

* Maps
 * Textures
 * Map models
 * Map sounds
 * Skyboxes

### Unlimited types of game modes

* The game logic must be loaded dynamically (for example a javascript)
* Game mode configuration
 * spawn/respawn states
  * team modifiers
  * specify allowed weapons, ammo, reload time, ...
  * specify health, armor, ...
 * specify engine/physics modifiers
* API for adding features to the HUD
 * New elements on the HUD
 * Minimap

### Destructible geometry

* Modify geometry
 * Shot based
 * Explosion based
* Modify lightmaps
* Synchronize geometry of all players
* Synchronize lightmaps