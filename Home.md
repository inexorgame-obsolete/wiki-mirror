# Inexor Documentation

![Error:Inexor logo not found!](https://raw.githubusercontent.com/inexorgame/site/master/src/assets/logo_rendered/inexor_logo_600.png)

## The Vision

There are possibilities only an open-source game can offer.  
There are ways only those can walk, who are not afraid of their ideas being stolen.

We want to create a game which allows people to create the game.  
To make it their own.  
To have fun learning continuously more stuff as they dig deeper into making it their own.  
And also: to develop the right mindset to attack challenging opportunities.
This includes doing stuff cooperatively.  
Inexor will always try to bring people together. There is no (official) single player planned.

_See also:_
* _[[The Main Theme]]_
* _[The Coding philosophy](https://github.com/inexorgame/inexor-core/wiki/Home/_edit#coding-philosophy)_

## The Background

We do not start from scratch. We derived from the famous open-source game [Cube2: Sauerbraten](http://sauerbraten.org/), which already went this walk a good distance.
Including an ingame map creator, a unique and fun gameplay and a friendly community, it gives us a head-start

The obvious advantage is that we always have something playable, even in times we consider ourselves not-yet-arrived.

We forked off from Sauerbraten when its development died. We find the ideas of Sauerbraten worthy enough to sustain in a new game.
The code-base has aged of course, but as we continue renewing it towards being easier to work with, we will be able to implement a lot of modern ideas and unique solutions.

## The Connection

#### Coding philosophy

To begin with, [refactoring](https://en.wikipedia.org/wiki/Code_refactoring) the old Cube2 code is essential.
You can find a lot of the "write it from scratch in C"-philosophy in Sauerbraten's code.
We are not afraid of using modern methods and libraries whenever it's appropriate to achieve our goal.
Therefore, we shall consider the following aspects of development:

1. **documentation**: always [[document|Documentation]] your work
2. **simplicity**: make it as easy as possible (only as complicated as needed)
3. **modularity**: write your code in [[modules]]
4. **maintenance**: make it easy to maintain (for someone else!)
5. **partitition** split your work up into small files
6. **consistency**: don't replicate code parts and try to use standard libraries
7. **communication**: tell other team members about your work

You should also take a look at our [[Overall Architecture]].

#### Project strategy

The structure of a game like Inexor could be exemplary (and highly incomplete) displayed as follows:


_**Most widely effecting parts on the bottom, most visible parts at the top**_

![strategy pyramid](https://rawgit.com/inexorgame/visualisations/master/jobs/a_teamate_strategy_pyramid.svg)

Those bottom systems are giving the major direction, while the higher parts have to act in the frame of the lower choices.

On the other hand, the parts on the top are the ones which define the end-product, the ones the normal player will remember.

Generally speaking we want to renew stuff in bottom-up order, as we think the whole codebase has too many flaws to be ready for our goals.  
However, we do not want to remain in the state of creating an engine, without providing the Sauerbraten people with something they can play.
Hence it's an iterative process to get the fundamental back-end _ready enough_ and providing features on the front-end with that new back-end functionality.

We want to keep a playable state.

-----------

For more information see the
## [FAQ](https://github.com/inexorgame/code/wiki/Frequently-Asked-Questions)

## Objectives

* Keep this old school game with its' classic gameplay alive
* Discuss and implement community ideas
* Reach the audience this game deserves
* Make it 100% [open source software](https://creativecommons.org/about/program-areas/technology/technology-resources/software/) and free of restricting licenses

### How to get involved
* [[How to Contribute Code]]
* [[How to Contribute Content]]  
* [[Recruiting]]

### Development

* [[Build]]
* [[Directory Structure]]
* [[Contact]]
* [[Coding Standards]]
* [[Documentation]]
* [[How To Debug]]
* [FAQ](https://github.com/inexorgame/inexor-core/wiki/Frequently-Asked-Questions)

## Features

* [Milestones](https://github.com/inexorgame/code/milestones) / [Changelog](https://github.com/inexorgame/code/blob/master/changelog.md)
* [[Sauerbraten Features]] (this is where we started)
* [Ideas for Features](Feature-Ideas)

####  DONE

| Subsystem    | Topic                                                    | [Core](Inexor-Core) | [Flex](Inexor-Flex) | [UI](Inexor-UI) |
| ------------ | -------------------------------------------------------- | -------- | -------- | -------- |
|              |
| Synchronisation  | [Generic RPC Subsystem + Node.js integration](RPC-Node.js) | &#10003; | &#10003; |        |
|              | [[Inexor-Tree]] (Proposal: [[Inexor Tree API]])          | &#10003; | &#10003; | &#10003; |
| Overall      | [[Logging]]                                              | &#10003; | &#10003; |          |
| Build        | [[Build]]                                                | &#10003; |          |          |
|              |

####  IN PROGRESS

| Subsystem    | Topic                                                    | [Core](Inexor-Core) | [Flex](Inexor-Flex) | [UI](Inexor-UI) |
| ------------ | -------------------------------------------------------- | -------- | -------- | -------- |
|              | 
| UI           | [[HTML5 User Interface]]                                 | &#10003; | &#10003; |          |
|              | [[Keyboard and mouse input handling]]                    | &#10003; | &#10003; | &#10003; |
|              | [[User interface Menu]]                                  |          | &#10003; |          |
| Entities     | New [[Entity System]]                                    | &#10003; | &#10003; |          |
|              | [[Particle System]]                                      | &#10003; | &#10003; |          |
|              | [[3D Visual Scripting]]                         | &#10003; | &#10003; |          |
|              | [Bezier curve camera flights](Bezier-curve)              | &#10003; |          |          |
| Rendering    | [[Shader System]]                                        | &#10003; | &#10003; |          |
| Server       | [Server refactoring](Refactoring-The-Server)             | &#10003; |          |          |
| Config       | [JSON configuration support](JSON-Implementation)        |          | &#10003; |          |
| Editing      | [[Version Control System]]                               | &#10003; |          |          |
| Audio        | [[New Sound system (refactoring)]]                       | &#10003; |          |          |
| Release      | [[Release and build strategy]]                           | &#10003; | &#10003; |          | 
|              |
| **Planned**  | 
|              | 
| Overall      | [[Make anything more dynamic]]                           | &#10003; | &#10003; | &#10003; |
| Content      | [[Distributing Content System]]                          |          | &#10003; |          |
| World        | [[Extendable Map Format]]                                | &#10003; |          |          |
| Rendering    | [[Dynamic Lighting]]                                     | &#10003; |          |          |
| Editing      | [[Improved Selection]]                                   | &#10003; |          |          |
|              | [[Mappers Toolset]]                                      | &#10003; | &#10003; | &#10003; |
| Multiplayer  | [[Decentralized server list]]                            |          | &#10003; |          |
| Multiplayer  | [[Self regulating distributed network]]                  |          | &#10003; | &#10003; |
| Distribution | [[Packaging]]                                            |          |          |          |

