# 3 dimensional flowchart level scripting

Sauerbraten's maps (in multiplayer mode) are horribly static:

* No destruction of geometry
* No interaction with geometry
* No event triggers
* No timers
* No buttons or interaction keys
* No doors/elevators...
* No change of enviroment parameters (light intensity...)
* No script<->code devices to play sounds or make console output e.g.

Sauerbraten comes with a very raw and basic script architecture which is sufficent for single player levels.
I want to create a new interface for level-embedded scripting.

Visual scripting has many advantages compared with traditional code-editor scripting:
* It is easy and safe to use
* you can debug your code visually
* It can be converted to any script language you want (LUA e.g.)

A very common form of visual scripting are flowchart editors.
Strangely most flowchart editors are two-dimensional. You can create your
program flow on a 2d layer. I always wondered why there is not a single 3D flowchart editors in
big engines (such as Unity, CryENGINE..)
I want to prove that 3d flowchart editing increases clearness and visbility of your code.

## Developers

Hanni

## Features

* Level-embedded 3D scripting
 * Debugmode
 * bridges between Sauerbraten's functions and script function calls (similiar to cubescript)
 * function timers
 * event triggers
 * 3D objects that represent script blocks and tokens
 * script exporter (LUA)
 
(to be continued...)