*This page is work in progress*

### Goals

* User interface in standard HTML5 / JavaScript
* Deep integration of the UI technology
* Multiple layers
* Console
* Main menu
* Input events (mouse and keyboard)

[![Improved particle system video](http://img.youtube.com/vi/eFMS_bXPDr8/0.jpg)](http://www.youtube.com/watch?v=eFMS_bXPDr8)

### Developers

* Hanack
* mapc
* a_teammate
* Hanni

### Idea

* Rendering of HTML5 over a transparent 2D-Overlay
* Spawning events from HTML5 / client side JavaScript
* see also [#50](https://github.com/inexor-game/code/issues/50)

### Chromium Embedded Framework

* https://bitbucket.org/chromiumembedded/cef
* http://coherent-labs.com/blog/what-developers-should-consider-when-using-chromium-embedded-framework-cef-in-their-games/
* http://blog.erikd.org/2013/01/14/chromium-embedded-framework-3-bare-bones/

### Architecture

* EventManager
* LayerManager
* ContextManager

## We have a basic working framework!

This introduces a basic, working framework that will be used to render Web guis with node.js and cef.

### What it can do

* Dependency management with node_modules, requirejs and angular
* Node modules are available in the browser with a browserify/requirejs bridge (so we do not have to dump external libraries in our repo)
* Uses express.js in the server
* Uses jQuery
* Uses lodash
* Uses Bootstrap
* Uses Angular.js
* Supports Coffeescript
* Supports Jade
* Supports Stylus
* Create angular directives as coffeescript classes, with automatically loaded CSS (stylus) and HTML (jade) files
* Window management

### What it can not do

* Both the mouse movement processing of the window manager and the one by our cef implementation are very bad; moving windows is a bit harsh.
* We will need to do a lot of refactoring
* Actual data exchange between inexor <-> node <-> the weg GUI; we can not implement any real functionality atm (though that can be helped quickly)
