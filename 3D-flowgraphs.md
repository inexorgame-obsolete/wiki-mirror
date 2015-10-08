# Motivation
## What are Scripts and why are they important?
Modern Embedded Scripting Languages deliver **flexibility**, **variety** and infinite room for **creativity** in game levels. They have other applications as well: What would the World Wide Web be without Javascript running fast as hell in your browser in this very moment?

Here is a list of very common Scripting Languages with various applications:
* [Javascript (for client-side website scripting and much more)](http://www.w3schools.com/js/default.asp)
* [Python (various applications)](https://www.python.org/)
* [Perl (various applications)](https://www.perl.org/)
* [Ruby (various applications)](https://www.ruby-lang.org/)
* [Google GO (Google's new language)](https://golang.org/)
* [PAWN-Script(for microprocessor stuff)](http://www.compuphase.com/pawn/pawn.htm)
* [PHP (for webservers)](https://php.net)

Scripts only run on your system if you have the right *interpreter* which can *interpret* the script code.
That distinguishes Scripting Languages from *Compiled Code*. Compiled code (such as the Inexor game) is produced with a *compiler* that writes everything together in a static binary that can't change anymore.
Inexor has Google's V8 Javascript Engine (this is such an interpreter..) embedded which is probably the fastest Javascript interpreter that exists. 

Though compiled code *tends* to be a little faster than scripts, it can't be changed anymore afterwards whereas scripts could be **edited by YOU anytime**. 
Plus the execution speed difference (especially for small scripts) is getting smaller every year because new technologies and faster Computers come up.

## How are scripts being used in games?
No matter what games you play: everything that provides interaction and is not hardcoded is *scripted*.
Most games deliver their level scripts included directly in the maps.
The following shows various uses for script in games:
![Illustrations of various Scripting systems in use.](https://raw.githubusercontent.com/inexor-game/visualisations/17dd68a0625130212d58828e573a1b60b169078e/3D%20flowgraph/wiki/script_examples_1.png)

## What does Cube2: Sauerbraten offer us?
Unfortunately, Sauerbraten's code base does not come with any high level scripting language.
All we have is **Cubescript**. It was invented around ten years ago when writing your own language was cooler and than using libraries and frameworks. Cubescript may have its advantages, but it is 

* hard to understand
* maybe contains security issues or bugs due to the missing reviews.
* and barely documented. 

The advantages of Javascript are obvious:

* its being used all over the globe
* its a high level programming language
* its simple
* its fast
* its easy to learn

These are the reasons why we decided to **replace Cubescript with Javascript.**

## What is Visual Scripting
But what if writing code and game logic gets even cooler and easier??

## Why should we make Visual Scripting 3-dimensional?
*Because it has never been tryed before!*
