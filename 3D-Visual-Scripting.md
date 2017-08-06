Branches | Issues | Main developers
--- | --- | --- 
[hanni/3DVisualScripting](/inexorgame/code/tree/hanni/3DVisualScripting) |  [#99](/inexorgame/code/issues/99), [#111](/inexorgame/code/issues/111) | [@IAmNotHanni](/IAmNotHanni)

# Introduction
This article was written for somebody without any experience in the field of scripting. After a general discussion it leads on to the architecture of Inexor's 3D visual scripting system. 

## What is a script in general?
Scripts allow you to change the logic of a game (or a program in general) without having to change one line of C/C++ source code. Scripts will not be compiled directly into a binary executable like an exe file, they will be processed by an [interpreter](https://en.wikipedia.org/wiki/Interpreter_(computing)). Usually they are easier to learn than high level programming languages.

One of the most popular [scripting languages](https://en.wikipedia.org/wiki/Scripting_language) is [JavaScript](https://en.wikipedia.org/wiki/JavaScript) which for example runs in your browser while you are reading this. Thanks to the integration of [NodeJS](https://nodejs.org/en/) (see [[Inexor-Flex]]) we have the full power of Javascript available in our engine as well. NodeJS runs on [Google's V8 engine](https://developers.google.com/v8/) which powers Google Chrome.

## How are scripts being used in games?
The big part of the game logic in modern games - from simple player interactions (for example a button that opens a door) to complex systems (for example artificial intelligence controllers) - is scripted. The biggest benefit of this is that **the development of the game itself (the map and its logic) can be separated from the development of the game engine**! The game engine delivers the tools which content creators then use.

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/a10c0c475f5b663e13fb39b5404ca174ad887b04/wiki/scripting_illustration.png)

## What are the benefits?

#### development speed
You don't have to recompile your code into a new binary every time you've made a change. You can test everything in realtime. Modern scripting languages offer code execution with a speed that is similar to assembly code.

#### simplicity
Scripting frameworks offer you predefined events, functions and access to variables. Everything is already there. You just have to put it together which requires much less knowledge about the technology behind it.

#### portability
Scripts can be interpreted on every [platform](https://en.wikipedia.org/wiki/Computing_platform) (Windows, Linux, Mac..) where an interpreter is available. You can test your script on one platform and be assured that it will work on every other platform as well. Making sure your C/C++ source code works everywhere on the other hand is usually a very hard job. Interpreters are available for all platforms and the engine developers make sure its working for you!

#### multithreading
Script tasks can be started in their own [thread](https://en.wikipedia.org/wiki/Thread_(computing)) which helps to distribute processor usage.

## Example scripts
Imagine you would like to add a **button** to your map that opens **door 1** and plays a sound as soon as a player pressed it. This could be done with the following script:

```
callback OnPlayerPressButton(player, button)
{
    OpenDoor(1);
    PlaySound('door_open');
}
```

Here's another example:
imagine an **explosive barrel** that blows up when you shoot it. The barrel also explodes when somebody pushes a **button**. It could be done with the following script:

```
callback OnPlayerShootsBarrel(player, barrel)
{
    CreateExplosion();
}

callback OnPlayerPressButton(player, button)
{
    CreateExplosion();
}
```

## What is visual scripting?
Visual scripting takes all this to the next level. Every script code can be expressed as a [graph](https://en.wikipedia.org/wiki/Graph_theory)!
Instead of writing your script code in a text editor, you just playfully put together specific **relations** between certain **nodes** to a **graph**. It is the types of nodes and their relations with each others that represent a script code. To illustrate this, the 2 code examples from above have been "rewritten" into the following corresponding visual script:

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/3270f1200c37d38ec0880c974373490996203d84/wiki/vs_graph_example_1.png)

As you can see an event emitter node (here OnPlayerPressButton) starts code execution. The direction and flow of execution is indicated by the green arrows, the red arrows show parameter references. A full explanation of this can be found in the section "graphic design of visual scripting" below.

Here is the visual script for the second example:

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/1a8044eb19f87aab5fdefc6a6c16edf54f3565c4/wiki/vs_graph_example_2.png)

Two event emitter nodes will cause the same function call. This visual script represents the idea that both shooting the barrel and pressing the button will cause the explosion.

## What are the benefits of visual scripting?

#### even more simplicity
A visual scripting enviroment offers everything you need but still stays simple to use. 

#### visually appearing working enviroment
Visual scripting is fun! You primarily work with your mouse to connect nodes playfully. You don't have to type that much on your keyboard anymore. It's much easier to look at a big visual script than to look a long lines of code.

#### visual debugging
It' much easier to illustrate code execution in a visual script. We will come back to this later on.

#### No syntax errors anymore!
The visual scripting system exactly controls how nodes are linked together. [Syntax errors](https://en.wikipedia.org/wiki/Syntax_error) like in the following example are not possible in a graph representation of script code:

```
callback OnPlayerPressButton player) // syntax error: forgot (
{
    // Heal the player as soon as he presses the button
    RestorePlayerHealth(player);
}
```

Logic errors however are still possible. Neither a compiler nor an interpreter can discuss the logic of your code. If your intention is to kill the player as soon as he hits the button although you programmed it to heal him that's an example for a logic mistake!

## How important is visual scripting used in modern game engines?

Every modern game engine has a visual scripting enviroment. [Unreal Engine 4 ](https://www.unrealengine.com/en-US/blog) (epic games) for example has a system called [Blueprint](https://docs.unrealengine.com/latest/INT/Engine/Blueprints/) (formerly called Kismet). CryEngine (Crytek GmbH) has a visual scripting enviroment called [Flowgraph](https://www.cryengine.com/features/sandbox-tools#features/flowgraph).

## Conclusion
Inexor needs a visual scripting system. Because Inexor supports [CEF (Chromium Embedded Framework)](https://bitbucket.org/chromiumembedded/cef) we have all we need for HTML5 visual scripting enviroments. In 2D it could be done using [visJS](http://visjs.org/).

# 3D Visual Scripting!
Now that we have discussed visual scripting in 2 dimensions, lets go one step further. All those programming concepts can be applied in 3 dimensions as well! 
In most other visual scripting systems the **graph** is edited in a planar 2D window that is separated from the game world. However it is intuitive to place script code (= **nodes** and **relations**) at the place where it affects the game world!
> **The map itself is our visual scripting enviroment!**

## Proof of concept
A very basic system has already been implemented but the final implementation will start from scratch again. This time _everything_ will be planned before implementing it.

In the following youtube video you can see a spheric area. A console message will appear once you enter or leave the area.

[![error: image not found](https://img.youtube.com/vi/4GuqvjhE_Gw/0.jpg)](https://www.youtube.com/watch?v=4GuqvjhE_Gw)

## Name?
Inexor's 3D visual scripting system needs a keyword as a name. Just like "Inexor Flex" stands for NodeJS integration.

### Idea 1: FEYNMAN

![error:image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/d2f9d6cd1beae855f01710c931f2a0da0d262c44/feynman/feynman_logo.png)

To name Inexor's visual scripting enviroment after physicist and nobel price winner _Richard Feynman_ would be an appropriate suggestion. Feynman was one of the most brilliant scientists of the 20st century and he had a neck for illustrating complex things with easy models. He got famous for his [Feynman Diagrams](https://en.wikipedia.org/wiki/Feynman_diagram) which are still used today.

The have not much in common with a graph for game logic but they look quite similar.

### Idea 2: AGENDA
TODO

### Idea 3: FEMTO
(=Flowgraph Editing Multi Tool)

### Idea 4: VAPE
(=Visually Appearing Programming Enviroment)
Because you'll become addicted to it

# Architecture
TODO

## Terminology
There are various different **types** of nodes and each has their specific **attributes** and **methods**.

* An **attribute** represents a property of a node.
* A **method** is something a node can do. method may accept **parameters**.

TODO
