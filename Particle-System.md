In sauerbraten-fork we are about to implement an improved particle system.

## Features

* Good performance though very dynamic
* Generic abstraction layers
** Multiple stateful and dynamically configurable particle emitter types
** Multiple stateful and dynamically configurable particle renderer types
** Multiple stateful and dynamically configurable particle modifier types
* Stateful particles
* A rich set of useful emitters, renderers and modifiers

### Particle Emitter Implementations

* Point
* Line
* Plane
* Circle
* Sphere
* 2D Raster Field
* 3D Raster Field

### Default Emitter Attributes

* Emitter rate
* Initial Velocity
* Scatter
* Renderer to use
* Modifiers to use

### Particle Modifiers Implementations

* Mass-Spring
 * Particle <-Spring-> Particle
 * Fixed Coordinate <-Spring-> Particle
* Brownian Motion
* Velocity Damper
* Branching Particles
* Bounding Box Particle Culling
* Geometry Collision (expensive)

### Particle Rendering Implementations

* Point-Based (Billboards)
 * Smoke
 * Fire
 * Lava
 * Poison
 * Snow
 * Flares (Lightnings, Rain)
* Geometry-Based
 * 2D: Triangles, Quads, Rings, ...
 * 3D: Tetrahedrons, Cubes, Tubes (Hair), ...
* Faces-Based or Model-Based
 * Textured quads: 4 particles belong to a face
 * Meta Balls: merge multiple particles into a blub

### Particle Modifier Implementations

* Gravity Points, Planes (only applies on particles)
 * Constant Gravity
 * Pulsing Gravity

### Performance Considerations

* Use pools
* Use shaders
* Use billboarding
* Particle Limiter
* Particle Culling

### Full control for map makers

* Scripting particle effects using JavaScript / Lua /whatever
* Modify emitter attributes
* Modify modifier attributes
* React on player position
