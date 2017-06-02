# Inexor Documentation

## [FAQ](https://github.com/inexor-game/code/wiki/Frequently-Asked-Questions)
 
## Objectives
_Stays Sauer, becomes better._

* Fork of Sauerbraten in order to replace Sauerbraten - no mod
* Bigger audience for the game
* Keep the game alive for the future
* 100% Open Source software (OSS), no restricted licensed content

## Philosophy

Our philosophy is making maintenance as easy as possible.

Hence we try to make the code easier understandable and easier to dive into.  
However some changes (e.g. regarding our [[Overall Architecture]]) add _some_ complexity to make team-development easier,
i.e. modularity has been introduced as a general concept we try to follow.

We are not afraid of using modern methods and libraries where appropriate to achieve our goal of a next-gen game.  
(The traditional view in the C-world is to write things from scratch)

Creating Inexor is traditionally part of the game. It was that way before in Sauerbraten (in form of creating maps ingame) and we are aiming to improve on that.

## Renewal Strategy

The structure of a game like Inexor could be exemplary (and highly incomplete) displayed as follows:


_**Most widely effecting parts on the bottom, most visible parts at the top**_

![strategy pyramide](https://rawgit.com/inexor-game/visualisations/master/jobs/a_teamate_strategy_pyramid.svg)

Those bottom systems are giving the major direction, while the higher parts have to act in the frame of the lower choices.

On the other hand, the parts on the top are the ones which define the end-product, the ones the normal player will remember.

Generally speaking we want to renew stuff in bottom-up order, as we think the whole codebase has too many flaws to be ready for our goals.  
However we do not want to remain in the state of creating an engine, without providing the Sauerbraten people with something they can play.
Hence its an iterative process to get the fundamental back-end _ready enough_ and providing features on the front-end with that new back-end functionality.

We want to keep a playable state.


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

### Other

* [Other Existing Projects](Other-Projects)
* [Website](https://inexor.org)
* [[Contact]]


## Features

* [Milestones](https://github.com/inexor-game/code/milestones) / [Changelog](https://github.com/inexor-game/code/blob/master/changelog.md)
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
|              | [[Visual Scripting Environment]]                         | &#10003; | &#10003; |          |
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
