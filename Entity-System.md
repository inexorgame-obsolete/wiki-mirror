Branches | Issues | Main developers
--- | --- | --- 
[NewEntities](/inexor-game/code/tree/NewEntities), [cef+entities](/inexor-game/code/tree/cef+entities), [rebased-cef+entities](/inexor-game/code/tree/rebased-cef+entities), [cef+ipc+entities](/inexor-game/code/tree/cef+ipc+entities), [cef+ipc+entities+bezier](/inexor-game/code/tree/cef+ipc+entities+bezier) |  [#111](/inexor-game/code/issues/111) | [@aschaeffer](/aschaeffer), [@super-tux](/super-tux) 

### The goal

The goal is to implement a new entity system which will provide a solid basis for other so called subsystems like mapmodels, the Visual Scripting Enviroment or the particle system (and many more).

## AttributeBase

![AttributeBase](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/AttributeBase.png)

## AttributeRefPtr

![AttributeRefPtr](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/AttributeRefPtr.png)

## EntityAttribute

![EntityAttribute](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/EntityAttribute.png)

## EntityFunction

![EntityFunction](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/EntityFunction.png)

## EntityInstanceManager

![InstanceManager](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/EntityInstanceManager.png)

## EntityTypeFactory

![EntityTypeFactory](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/EntityTypeFactory.png)

## EntityTypeManager

![EntityTypeManager](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/EntityTypeManager.png)

## EntityTypeProvider

![EntityTypeProvider](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/EntityTypeProvider.png)

## FunctionRefPtr

![FunctionRefPtr](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/FunctionRefPtr.png)

## InstanceRefPtr

![InstanceRefPtr](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/InstanceRefPtr.png)

## ParticleWorker

![ParticleWorker](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/ParticleWorker.png)

## RelationshipTypeProvider

![RelationshipTypeProvider](https://raw.githubusercontent.com/inexor-game/visualisations/45f342299fce76f3ea603c745da0cfbade201a85/hanacks%20entity%20and%20particle%20system/RelationshipTypeProvider.png)

### Entities are used for

* players
* mapmodels
* mode specific entities: flags, bases, ...
* player state changing pickups: ammo, armor, health, ...
* weapons and bouncers: grenades, rockets, fog grenades, ...
 * grenades
  * grenade launcher = particle emitter instance
  * grenade = particle
  * plus geometry collision particle modifier
 * decals
  * special type of particles
  * decal particle renderer
 * explosions, splinter
  * volumetric expansion of explosions (also using the densitiy attributes)
* particle system entities
 * particle emitter instance
 * particle modifier instance
 * particle renderer instance
* event system entities
 * positional trigger
  * positional entity

## Entities itself

* consists of named attributes
 * like position, velocity, states, ...
* attribute inheritance ?
* entity graph
 * parent/child relationships between entities (particle modifier instances --[n:m]--> particle emitter instances)
* event handling
 * publisher / subscriber pattern
 * triggers events

### Management of entity attributes

* which attributes have to be persisted
* which attributes have to be synchronized over network
* specification of the data type of an attribute value
* how to persist attributes (along with the map)
* how to synchronize attributes over network (using network messages)

### Entity emitter

* Emits entities
* Use case: pickup emitter for ammo:
 * spawns ammo pickup of a configurated type in a specific rate
 * bind the spawned pickup entity (add child)
 * as long as the child isn't picked up, don't spawn other pickups

### Entity modifier

* modify(entity)
* modifies attributes of an entity
* create events based on an entity
 * player entity near entity modifier
 * Flag stolen
 * Flag near player
 * Base captured
* entity movement
 * Move along segmented paths (bezier curve)
  * Path: Segments
  * Segment: Start, End, Speed
* Particle emitter configuration
