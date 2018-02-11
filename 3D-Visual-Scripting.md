Branches | Issues | Main developers
--- | --- | --- 
[hanni/3DVisualScripting](/inexorgame/code/tree/hanni/3DVisualScripting) |  [#99](/inexorgame/code/issues/99), [#111](/inexorgame/code/issues/111) | [@IAmNotHanni](/IAmNotHanni)

# Introduction
This article was written for readers without any technical knowledge of scripting. The objective is to introduce some important ideas behind scripting languages. This is the foundation for the understanding of Inexor's 3D visual scripting system.

## What's a script?
Scripts allow you to write program code without having to edit and recompile the source code. Scripts will not be compiled into an executable file, instead they will be processed by an [interpreter](https://en.wikipedia.org/wiki/Interpreter_(computing)). This means script code can be changed after the program in which the interpreter is embedded has been compiled. Script code can even be changed while the program is running. [Scripting languages](https://en.wikipedia.org/wiki/Scripting_language) are usually easier and faster to learn than high level programming languages like C++.

One of the most popular scripting languages is [JavaScript](https://en.wikipedia.org/wiki/JavaScript), which runs in your browser while you are reading this. Javascript made the development of modern websites possible and every popular website uses it today. After this the development of [NodeJS](https://nodejs.org/en/) had a big impact on developers because it makes it possible to use Javascript to write desktop applications. NodeJS runs on [Google's V8 engine](https://developers.google.com/v8/) which powers Google Chrome. Since [NodeJS](https://nodejs.org/en/) (see [[Inexor-Flex]]) is integrated into Inexor we have the full power of Javascript available as well.

## How are scripts being used in games?
The big part of the game logic in modern games - from simple player interactions (for example a button that opens a door) to complex systems (for example artificial intelligence controllers) - is scripted. The biggest benefit of this is that the **development of the game itself (the map and its logic)** can be **separated** from the **development of the game engine!** The game engine delivers the tools which content creators then use.

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/a10c0c475f5b663e13fb39b5404ca174ad887b04/wiki/scripting_illustration.png)

**Scripts are essential for a dynamic gameplay design!**

## What are the benefits?

#### simplicity
* Scripting requires less knowledge about the technical backgrounds.
* Javascript for example is easy to learn
* The **scripting framework** gives you everything you need: events, functions, variables..

#### development speed
* You don't have to **recompile** your code into a new binary every time you've made a change.
* You can test everything in **realtime**. You don't have to restart the game itself every time.
* Modern scripting languages offer code execution with a speed that is similar to assembly code.

#### security
* Javascript code runs in a **sandbox** which acts like a security layer between script and your computer. 
* Executing someone elses script is less dangerous than compiling and executing C/C++ code someone else!
* The chance of a game crash is reduced. At worst your script won't work.

#### portability
* Scripts can be interpreted on every [platform](https://en.wikipedia.org/wiki/Computing_platform) (Windows, Linux, Mac..) where the required interpreter is available.
* You can test your script on one platform and be assured that it will work on every other platforms as well.
* Making sure your C/C++ source code works on other Platforms ("_porting_" the code) on the other hand is usually a (very) hard job.

#### multithreading
* Script tasks can be started in their own [thread](https://en.wikipedia.org/wiki/Thread_(computing)) which helps to distribute processor usage.

## Example scripts
Imagine you would like to add a button to your map that opens door 1 and plays a sound as soon as a player presses it. This could be done with the following script:

```
callback OnPlayerPressButton(player, button)
{
    OpenDoor(1);
    PlaySound('door_open');
}
```

Here's another example:
imagine an explosive barrel that blows up when you shoot it. The barrel also explodes when somebody pushes a button. It could be done with the following script:

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
Instead of writing your script code in a text editor, you just playfully put together specific **relations** between certain **nodes** to a **graph**.

**It is the types of nodes and their relations with each others that represent a script code.**

To illustrate this, the first code example from above has been "rewritten" into the following corresponding **visual script**:

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/aa4aa88812784dbb473c2e16c75a4e3d39c187ec/wiki/vs_graph_example_1.png)

What you may noticed already:
* An event node (here OnPlayerPressButton) starts code execution.
* The direction of execution is indicated by the arrows (= **relations**) which are green, the red arrows show parameter references.

Here is the visual script for the second example:

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/4ce7e69803cbc25eb95a41ffaf1f22f1143f887e/wiki/vs_graph_example_2.png)

Two event emitter nodes will cause the same function call. This visual script represents the idea that both shooting the barrel and pressing the button will cause the explosion.

## What are the benefits of visual scripting?
**Please remember that it's just another way of illustrating code! A visual scripting system is as powerful as script code in text form.**

> It is possible to transform the data from visual scripts to script code in text form. This means that we could transform our input data to javascript.

#### even more simplicity
* You primarily work with your mouse to connect nodes.
* You don't have to type that much on your keyboard anymore.
* Visual scripting is fun!

#### visually appearing work enviroment
* It's much easier to look at a big visual script than to look a long lines of code.
* Nodes can be grouped just like code can be split up into different files.
* It' much easier to illustrate code execution in a visual script. We will come back to **visual debugging** later on.

#### No syntax errors possible!
The visual scripting system exactly controls how nodes are linked together. [Syntax errors](https://en.wikipedia.org/wiki/Syntax_error) like in the following example are not possible in a graph representation of script code:

```
callback OnPlayerPressButton player) // syntax error: forgot (
{
    // Heal the player as soon as he presses the button
    RestorePlayerHealth(player);
}
```

> **Logic errors** however are still possible. Neither a compiler nor an interpreter can discuss the logic of your code. If your intention is to kill the player as soon as he hits the button although you programmed it to heal him that's an example for a logic mistake!

## How important is visual scripting for modern game engines?

Every modern game engine has a visual scripting enviroment. 
* [Unreal Engine 4 ](https://www.unrealengine.com/en-US/blog) for example has a system called [Blueprint](https://docs.unrealengine.com/latest/INT/Engine/Blueprints/) (formerly called Kismet).
* [CryEngine](http://crytek.com/) has a visual scripting enviroment called [Flowgraph](https://www.cryengine.com/features/sandbox-tools#features/flowgraph).
* [Blender](https://www.blender.org/) has a built in visual scripting enviroment called Blender Game Engine.
* [Unity](https://unity3d.com/de/) has a visual scripting editor available in the assets store.

> Visual scripting can also be used to create **GPU shaders** like vertex or pixel shaders!

# Visual Scripting in 3D!
Now that we have discussed visual scripting in 2 dimensions, lets go one step further. All those programming concepts can be applied in 3 dimensions as well! 
In most visual scripting systems the **graph** is edited in a planar 2D window that is separated from the game world. 
* Inexor disagrees with this concept and lets you place you nodes directly into the map!
* It is intuitive to place script code (= **nodes** and **relations**) at the place where it affects the game world!
* **The map itself is our visual scripting enviroment!**

## Proof of concept
In the following youtube video you can see a spheric area. A console message will appear once you enter or leave the area. Please note that this very basic implementation in 3D may looks different than the 2D graph examples from above but in essence this does represent a visual script!

[![error: image not found](https://img.youtube.com/vi/VC2eyxCNVfw/0.jpg)](https://www.youtube.com/watch?v=VC2eyxCNVfw)

Before the new system will be implemented everything should be _planned_ here in the wiki first!

## Inexor's 3D visual scripting system: AGENDA

go to the main page: [[AGENDA 3D Visual Scripting System]]