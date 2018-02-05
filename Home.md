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
Inexor will always try to bring people together.

_See also:_
* _[[The Main Theme]]_
* _[The Coding philosophy](https://github.com/inexorgame/inexor-core/wiki/Home/_edit#coding-philosophy)_

## The Background

We do not start from scratch. We derived from the famous open-source game [Cube2: Sauerbraten](http://sauerbraten.org/), which already went this walk a good distance.
Including an ingame map creator, a unique and fun gameplay and a friendly community, it gives us a head-start.

The obvious advantage is that we always have something playable, even in times we consider ourselves not-yet-arrived.

We forked off from Sauerbraten when its development died. We find the ideas of Sauerbraten worthy enough to sustain in a new game.
The code-base has aged of course, but as we continue renewing it towards being easier to work with, we will be able to implement a lot of modern ideas and unique solutions.

## The Connection

The structure of Inexor can be displayed as follows:


_**Most widely effecting parts on the bottom, most visible parts at the top**_

<img src="https://raw.githubusercontent.com/inexorgame/visualisations/master/wiki/Inexor-structure.svg?sanitize=true" />

Those bottom systems are giving the major direction, while the higher parts have to act in the frame of the lower choices.

On the other hand, the parts on the top are the ones which really impact the end-product, the ones the normal player will remember.

We have the advantage that some systems do not necessarily need to be renewed for our plans to be fulfilled sufficiently.  
And we have the time to iteratively create systems, and the freedom to improve their maintainability and usability until they are considered done.

Generally speaking we want to create and renew stuff in bottom-up order, as those low-level changes have the most impact over the whole system.

---

Developing software always includes thinking about the level of abstraction you want to keep in each layer.  
So how do we define seams? How to cut the system into logical chunks?

In our [[Overall Architecture]] page we give a clear rule for the first selection:  
* Is it performance-critical or not?

If not it should be moved to the [[Inexor Flex]]\(NodeJS\) part.  
If it is it can remain in the [[Inexor Core]]\(C++\) side.

Furthermore aiming for our goal of having a flexible sourcebase, we refactor and renew it following our [[Coding Standards]].

However, we do not want to remain in the state of creating an engine, without providing the Sauerbraten people with something they can play.  
Hence it's an iterative process to get the fundamental back-end _ready enough_ and providing features at the front-end (e.g. showcasing that new back-end functionality).

_We want to keep a playable state._  

See also:

* [[Coding Standards]]
* [[Overall Architecture]]
* [[Features]]


## Objectives

* Keep Sauerbraten's spirit alive
* Discuss community ideas, create creators
* Increase the old audience
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
