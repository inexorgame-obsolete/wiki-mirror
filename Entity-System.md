Branches | Issues | Main developers
--- | --- | --- 
[NewEntities](/inexor-game/code/tree/NewEntities), [cef+entities](/inexor-game/code/tree/cef+entities), [rebased-cef+entities](/inexor-game/code/tree/rebased-cef+entities), [cef+ipc+entities](/inexor-game/code/tree/cef+ipc+entities), [cef+ipc+entities+bezier](/inexor-game/code/tree/cef+ipc+entities+bezier) |  [#111](/inexor-game/code/issues/111) | [@aschaeffer](/aschaeffer), [@super-tux](/super-tux) 

## The goal

The goal is to implement a new entity system which will provide a solid basis for other so called subsystems like mapmodels, the Visual Scripting Enviroment or the particle system (and many more).

## Contents

1. [[Introduction|Entity System Introduction]]
2. [[Architecture|Entity System Architecture]]
3. [[Type System|Entity System Type System]]
4. [[Entity Graph|Entity System Graph]]

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
