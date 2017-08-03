Branches | Issues | Main developers
--- | --- | --- 
[hanni/3DVisualScripting](/inexorgame/code/tree/hanni/3DVisualScripting) |  [#99](/inexorgame/code/issues/99), [#111](/inexorgame/code/issues/111) | [@IAmNotHanni](/IAmNotHanni)

# Introduction
The following text was written for somebody without and knowledge about scripting at all. It starts with the very basics and leads to the architecture of Inexor's 3D visual scripting.

## What is a script in general?
Scripts allow you to change the logic of a game (or a program in general) without having to change one line of C/C++ source code. Scripting languages are easier to learn than high level programming languages. They are written in a [scripting language](https://en.wikipedia.org/wiki/Scripting_language) which is then processed by the [interpreter](https://en.wikipedia.org/wiki/Interpreter_(computing)).

One of the most popular scripting languages is [JavaScript](https://en.wikipedia.org/wiki/JavaScript) which for example runs in your browser while you are reading this. Thanks to the integration of [NodeJS](https://nodejs.org/en/) (see [[Inexor-Flex]]) we have the full power of Javascript available in our engine as well. NodeJS runs on [Google's V8 engine](https://developers.google.com/v8/) which powers Google Chrome.

## How are scripts being used in games?
The big part of the game logic in modern games has been scripted. From simple player interactions (like a button that opens a door) to complex systems (like artificial intelligence controllers). The biggest benefit is that the development of the game (map, level..) and its logic can be **separated** from the development of the game engine. The game engine delivers the tools which content creators (mappers..) then use.

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/1d5b631c2acb87235c2c997735253556f3c847e4/wiki/scripting_illustration.png)

## What are the benefits?
So why should we script the logic?
Why can't we just modify the source code?

### simplicity
Scripting frameworks offer predefined events, functions and access to variables. Everything is already there. You just have to put it together which requires little knowledge about what's behind it.

### speed
You don't have to recompile your binary every time you're making a change. You can test everything live. Most scripting interpreters like Google's V8 engine offer you high speed code execution.

### flexibility
Every important C/C++ function is available on the scripting side.

### multithreading
Timers and event emitters start code execution in their own thread which helps to distrubute the processor usage.

### portability
Scripts can be interpreted on every platform (Windows, Linux, Mac..) where an interpreter is available whereas making sure your C/C++ source code works everywhere usually is a hard job. Interpreters are available for all platforms and it's not your job as a game developer to ensure it is working. The engine developer take care of that for you!

## Examples
Imagine you would like to add a **button A** to your map that opens **door 1** and plays a sound once a player presses it. This is done with the following script:

```
callback OnPlayerPressButton(player, button)
{
    OpenDoor(1);
    PlaySound('door_open');
}
```

Once you save this script the interpreter will execute it. If you press button A **door 1** will open.

___

Here's another example:
imagine an explosive barrel that blows up when you shoot it. The barrel also explodes when somebody pushes **button B**.

```
function MyExplosion(barrel)
{
    CreateExplosion(barrel.pos);
    HideMapModel(barrel); // hide it because it has been destroyed
}

callback OnPlayerShootsBarrel(player, barrel)
{
    MyExplosion();
}

callback OnPlayerPressButton(player,button)
{
    if(button.name == 'B') MyExplosion();
}
```

## What is visual scripting?
Visual scripting takes all this to the next level. You no longer have to write code by hand with text editors, you put together so called **nodes** to a **graph**.

**It's the way you connect nodes with eachother that makes up the script code!**

To illustrate this, the two code examples from above have been "rewritten" into the following visual script:

![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/6676208ef61a704f2c7e7300ffd0f55a6f86c35b/wiki/vs_graph_example_1.png)

## Why 3D visual scripting?
TODO 

# Architecture
TODO

## Naming the system
Inexor's 3D visual scripting system needs a keyword as a name.

### Idea 1: FEYNMAN
To name Inexor's visual scripting enviroment after physicist and nobel price winner _Richard Feynman_ would be an appropriate suggestion. Feynman was one of the most brilliant scientists of the 20st century and he had a neck for illustrating the most complex things with in the easiest way. His Feynman Diagrams for example are still in use. The have nothing in common with a flowgraph for game logic but they look similar.

## Proof of concept
A very basic system has already been implemented.

## Terminology
There are various different **types** of nodes and each has their specific **attributes** and **methods**.

* An **attribute** represents a property of a node.
* A **method** is something a node can do. method may accept **parameters**.
