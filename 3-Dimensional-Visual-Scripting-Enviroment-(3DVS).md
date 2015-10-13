# Motivation
*Building a new form of creativity in Inexor*
## What are Scripts and why are they important?
Modern Embedded Scripting Languages deliver **flexibility**, **variety** and infinite room for **creativity** in game levels. They have other applications as well: What would the World Wide Web be without JavaScript running fast as hell in your browser in this very moment?

Here is a list of very common Scripting Languages with various applications:
* [JavaScript (for client-side website scripting and much more)](http://www.w3schools.com/js/default.asp)
* [Python (various applications)](https://www.python.org/)
* [Perl (various applications)](https://www.perl.org/)
* [Ruby (various applications)](https://www.ruby-lang.org/)
* [Google GO (Google's new language)](https://golang.org/)
* [PAWN-Script(for microprocessor stuff)](http://www.compuphase.com/pawn/pawn.htm)
* [PHP (for webservers)](https://php.net)

Scripts only run on your system if you have the right *interpreter* which can *interpret* the script code.
That distinguishes Scripting Languages from *Compiled Code*. Compiled code (such as the Inexor game) is produced with a *compiler* that writes everything together in a static binary that can't change anymore.
Inexor has Google's V8 JavaScript Engine (this is such an interpreter..) embedded which is probably the fastest JavaScript interpreter that exists. 

An example function written in JavaScript that returns the day of the week as a number:
![An example code written in JavaScript.](https://raw.githubusercontent.com/inexor-game/visualisations/f18a79c5a5297cb963759af1e2dc34317a0b1b55/3D%20flowgraph/wiki/JS_example_1.jpg)

Though compiled code *tends* to be a little faster than scripts, it can't be changed anymore afterwards whereas scripts could be **edited by YOU anytime**. 
Plus the execution speed difference (especially for small scripts) is getting smaller every year because new technologies and faster Computers come up.

## How are scripts being used in games?
No matter what games you play: everything that provides interaction and is not hardcoded is *scripted*.
Most games deliver their level scripts included directly in the maps.
The following shows various uses for script in games:
![Illustrations of various Scripting systems in use.](https://raw.githubusercontent.com/inexor-game/visualisations/17dd68a0625130212d58828e573a1b60b169078e/3D%20flowgraph/wiki/script_examples_1.png)

## What does Cube2: Sauerbraten offer us?
Unfortunately, Sauerbraten's code base does not come with any high level scripting language.
All we have is **Cubescript**. It was invented in 2005. We're not sure why they've decided to write their own scripting language instead of using existing implementations (probably because those weren't as developed as they're today?).
Cubescript may have its advantages, but it is 

* hard to understand (as someone who's used to C/C++/JavaScript)
* has some strange design decisions
* is very limited in its design
* maybe contains security issues or bugs due to the missing reviews
* and is barely documented

A script implementation for a singleplayer level in Sauerbraten's text editor:
![An implementation of a singleplayer level script.](https://raw.githubusercontent.com/inexor-game/visualisations/master/3D%20flowgraph/images/example_for_scripting_1.jpg)

The advantages of JavaScript are obvious:

* it's being used all over the globe 
* it's a high level programming language
* it's simple
* it's fast
* it's easy to learn
* and most importantly: **Cubescript was not designed for being used in multiplayer!** 

These are the reasons why we decided to **replace Cubescript with JavaScript.**

## What is Visual Scripting
But what if writing code and game logic gets even cooler and easier?
Code itself is nothing but a sequence of logic things. So why not include this into the level editor?
Here is a screenshot from [Unreal Engine 4](https://www.unrealengine.com/blog)'s "Blueprint" scripting system which is one of the leading technologies:
![Unreal Engine 4](https://raw.githubusercontent.com/inexor-game/visualisations/88345fe629936036a6469ffa628fed7d2e12e65c/3D%20flowgraph/wiki/visual_scripting_in_unreal_4.jpg)
In the right of the image there are all those blocks which are linked with lines. Every block (every **node**) stands for one code sequence (a command like "open a door", an "if" query or a game event). Relations between code blocks are represented by those lines.

Unreal Engine 4 describes the importance of their "Blueprint" script as follows:
## "*Blueprint visual scripting enables you to rapidly prototype and build complete games, simulations and visualizations without the need for programming. Blueprint tools and a visual debugger are included with Unreal Engine 4.*"

Here is another example from [CryEngine3 (Crytek GmbH)](http://cryengine.com/). The artificial intelligence of the player model is completely coded in the visual scripting enviroment(!):

![CryEngine3](https://raw.githubusercontent.com/inexor-game/visualisations/88345fe629936036a6469ffa628fed7d2e12e65c/3D%20flowgraph/wiki/visual_scripting_in_cryengine_3.jpg)

These are examples of 2-dimensional Visual Scripting Enviroments. All you need to learn is how to script with the front end tools and their user interface. The back end (how the script will be understood by your computer in detail) is the work of the game programmers.

## 3D Visual Scripting
**If you play in a 3D enviroment (the game world), why do we script on a plane screen in 3D??**
-That is a good question. Here is an example of level script that will be included *directly* into the game world (Doom 2016):
![Doom 4](https://raw.githubusercontent.com/inexor-game/visualisations/88345fe629936036a6469ffa628fed7d2e12e65c/3D%20flowgraph/wiki/visual_scripting_in_doom_4.jpg)

We may still not understand what this script does in detail, but seeing it in 3D placed in the game world is kind of relaxing. It is *part* of the level!. This is what we are planing to implement.

## Why should someone make Visual Scripting 3-dimensional?
* Because you can't make syntax mistakes, only *logic mistakes*!
* Because seeing code in 3D is way more relaxing and feels more naturally
* Because big 2D level scripts end up in a huge mess. An extra dimension would sort this thing up!
![An extra dimension would sort this mess up!](https://raw.githubusercontent.com/inexor-game/visualisations/66376b02eeddd0fb53bbcec60194044f2c00aa6d/3D%20flowgraph/wiki/hugemess.jpg)
* Because technically there is no difference between drawing those nodes in 2D or 3D! (the script works the same way)
* Because it allows us to debug *map parts* with their *code parts* visually!
* Because code parts that are linked with other things could be placed at those things (imagine a code which opens a door being put directly *at* the door)
* Because Inexor needs a Scripting System

## Further pages
[3DVS Design Decisions](3DVS Design Decisions)
* [Where does code execution start?](Where does code execution start?)
* [Limiting Recursion](Limiting Recursion)

[Node/Relation/Entity rendering](Node/Relation/Entity rendering)
* [Color codes for nodes](Color codes for nodes)

[Base class for nodes (script_node)](Base class for nodes)

[Derivates of script_node](Derivates of script_node)
* [About std::any](About std::any)
* [Timers](Timers)
* [Values](Values)
* [Memory](Memory)
 * [floating point (double/float)](floating point (double/float))
 * [(un)signed integers]((un)signed integers)
 * [Booleans](Booleans)
 * [strings](strings)
 * [vectors](vectors)
 * [unspecified](unspecified)
* [Math](Math)
 * [Simple Arithmetic operations](Simple Arithmetic oeprations)
  * [Increment and Decrement](Increment and Decrement)
 * [Functions](Functions)
 * [Trigonometry](Trigonometry)
 * [Vectors](Vectors)
* [If queries](If queries)
 * [Logic expressions](logic expressions)
 * [Switch queries](Switch queries)
* [Linked game functions](Linked game functions)
* [Events](Events)
 * [Linked game events](Linked game events)
 * [Collision areas](Collision areas)
* [Node to Javascript Transcompiler](Node to Javascript Transcompiler)
 * [Theory]
 * TODO..
* [Loops](Loops)
 * [While](While)
 * [For](For)
 * [Do]