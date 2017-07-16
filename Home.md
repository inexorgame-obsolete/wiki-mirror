# Inexor Documentation

_Stays Sauer, becomes better._

**What is it?**

* Inexor is a fork of the first person shooter [Cube2: Sauerbraten](http://sauerbraten.org/) aiming to replace it one day!
This project's name arised from our _inexorable_ efforts to reach our goal.

**Who are you?**

* We're all people from the old cube2 community. We are a group of programmers, mappers, artists..
See [this page](https://github.com/orgs/inexorgame/people) for more information.

**What created Inexor?**

* For over one decade now the cube2 community has seen astonishing projects trying to extract the maximum gameplay out of Sauerbraten. The amount and variety of the ideas the community came up with is impressive: from race maps, hide and seek, zombie apocalypse to rugby - nearly anything imaginable has been implemented.

* Nevertheless, the development of Cube2 is in the hand of a small circle of persons who are not open minded for new ideas or changes. We've seen so much great work being rejected from being included. It's their decision which ones are the good ideas and which ones are not. It's their decision which maps, game modes and features will make it into the releases and which ones won't.

* Speaking of releases, the release cycles have become longer and longer since 2008. The last Cube2 release until this day was in 2013. We have come to the conclusion that the development of Sauerbraten has reached its end.

* Inexor disagrees with this setup because we believe this is not suitable for an open source game!
The creative voices of the community remained unheard for too long.
We are the place where all these ideas can gravitate to so we can discuss them openly.

**Will it stay compatible with Cube2?**
* No. In the old days people came up with their own mods which were still compatible with the original game.
But it is this compatibility to Cube2 which obligated mod developers to stay within the old boundaries of the cube engine technologies. In order to make a new game we need to break up the old world. This is a fork, not a mod!

For more information see the
## [FAQ](https://github.com/inexorgame/code/wiki/Frequently-Asked-Questions)
 
## Objectives

* Keep this old school game with its classic gameplay alive
* Discuss and implement community ideas
* Reach the audience this game deserves
* Make it 100% [open source software](https://creativecommons.org/about/program-areas/technology/technology-resources/software/) and free of restricting licenses

## Coding philosophy

To begin with, [refactoring](https://en.wikipedia.org/wiki/Code_refactoring) the old Cube2 code is essential.
You can find a lot of "write it from scratch in C"-philosophy in Sauerbraten's code.
We are not afraid of using modern methods and libraries whenever it's appropriate to achieve our goal.
Therefore we shall consider the following aspects of development:

1. **documentation**: always [[document|Documentation]] your work
2. **simplicity**: make it as easy as possible (only as complicated as needed)
3. **modularity**: write your code in [[modules]]
4. **maintenance**: make it easy to maintain (for someone else!)
5. **partitition** split your work up into small files
6. **consistency**: dont replicate code parts and try to use standard libraries
7. **communication**: tell other team members about your work

You should also take a look at our [[Overall Architecture]].

## Project strategy

The structure of a game like Inexor could be exemplary (and highly incomplete) displayed as follows:


_**Most widely effecting parts on the bottom, most visible parts at the top**_

![strategy pyramide](https://rawgit.com/inexorgame/visualisations/master/jobs/a_teamate_strategy_pyramid.svg)

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
