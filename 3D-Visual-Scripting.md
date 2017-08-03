Branches | Issues | Main developers
--- | --- | --- 
[hanni/3DVisualScripting](/inexorgame/code/tree/hanni/3DVisualScripting) |  [#99](/inexorgame/code/issues/99), [#111](/inexorgame/code/issues/111) | [@IAmNotHanni](/IAmNotHanni)

# Introduction
The following text was written for somebody without and knowledge about scripting at all. It starts with the very basics and leads to the architecture of Inexor's 3D visual scripting.

## What is a script in general?
Scripts allow you to change the logic of a game (or a program in general) without having to change one line of C/C++ source code. Scripting languages are **easier to learn** than high level programming languages. They are written in a [scripting language](https://en.wikipedia.org/wiki/Scripting_language) which is then processed by the [interpreter](https://en.wikipedia.org/wiki/Interpreter_(computing)).

One of the most popular scripting languages is [JavaScript](https://en.wikipedia.org/wiki/JavaScript) which for example runs in your browser while you are reading this. Thanks to the integration of [NodeJS](https://nodejs.org/en/) (see [[Inexor-Flex]]) we have the full power of Javascript available in our engine as well. NodeJS runs on [Google's V8 engine](https://developers.google.com/v8/) which powers Google Chrome.

## How are scripts being used in games?
The big part of the game logic in modern games has been scripted. From simple player interactions (like a button that opens a door) to complex systems like artificial intelligence. The biggest benefit is that the development of the game and its logic can be separated from the development of the game engine. The game engine delivers the tools which content creators use to make their game.

## What are the benefits?
TODO

## Examples
Imagine you would like to add a button to your map that opens a door and plays a sound once a player presses it. This is done with the following script:

```
function OnPlayerPressButton(player,button)
{
    OpenDoor(1);
    PlaySound('door_open');
}
```

## What is visual scripting?
TODO 

## Why 3D visual scripting?
TODO 

## Name?
Inexor's 3D visual scripting system needs a keyword as a name.

### Idea 1: FEYNMAN
To name Inexor's visual scripting enviroment after physicist and nobel price winner _Richard Feynman_ would be an appropriate suggestion. Feynman was one of the most brilliant scientists of the 20st century and he had a neck for illustrating the most complex things with in the easiest way. His Feynman Diagrams for example are still in use. The have nothing in common with a flowgraph for game logic but they look similar.

# What's the plan
TODO 

## Proof of concept
TODO

# Architecture
TODO
