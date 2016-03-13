Branches | Issues | Main developers
-------- | ------ | ---
[cef](/inexor-game/code/tree/cef), [cef+entities](/inexor-game/code/tree/cef+entities), [cef+ipc+entities](/inexor-game/code/tree/cef+ipc+entities), [cef+ipc+entities+bezier](/inexor-game/code/tree/cef+ipc+entities+bezier), [rebased-cef+entities](/inexor-game/code/tree/rebased-cef+entities), [additional bug fix branches](/inexor-game/code/branches/all?utf8=%E2%9C%93&query=cef), [karo+fohlen+hanack/fix_cef](/inexor-game/code/tree/karo+fohlen+hanack/fix_cef) |  [#50](/inexor-game/code/issues/50), [#292](/inexor-game/code/issues/292) [Label: cef](/inexor-game/code/labels/cef) | [@aschaeffer](/aschaeffer), [@koraa](/koraa), [@a-teammate](/a-teammate), [@IAmNotHanni](/IAmNotHanni), [@Fohlen](/Fohlen)

### Goals

* User interface in standard HTML5 / JavaScript
* Rendering of HTML5 over a transparent 2D-Overlay (multiple layers)
* Forward SDL2 input events (mouse and keyboard) to the HTML5 browser
* Remove cube2's user interface build with cubescript
* Provide a single page application build with standard technologies and frameworks
* Use the model view controller pattern for implementing menus
* Use a framework for implementing a single page application
* Use a framework for implementing a responsive user interface
* Implementation of menus and HUDs
* Communicate with the Inexor application server (NodeJS) which is exposing the property tree as REST webservice

[![Early demonstration of Inexor with HTML5 user interface](http://img.youtube.com/vi/eFMS_bXPDr8/0.jpg)](http://www.youtube.com/watch?v=eFMS_bXPDr8)


### Used Technologies

#### Chromium Embedded Framework / HTML5 Rendering Engine

* With the "Chromium Embedded Framework" (CEF) we can embed the browser engine "Chromium" which is the open source project Google Chrome is built on
* The HTML5 technology is widely used and very suitable for Inexor and brings much more flexibility
* No need for a custom implementation of an user interface technology

##### CEF Resources

* https://bitbucket.org/chromiumembedded/cef
* http://coherent-labs.com/blog/what-developers-should-consider-when-using-chromium-embedded-framework-cef-in-their-games/
* http://blog.erikd.org/2013/01/14/chromium-embedded-framework-3-bare-bones/

#### AngularJS

* Model View Controller Pattern
* Two Way Data Binding (template and controller can modify objects)
* Dependency Injection (automatically wires dependencies at runtime)
* Single Page Application (a single page with inter page navigation)
* Templates, Directives, Expressions, Scopes, Filters, Modules
* A wide palette of angular modules (plugins) is available

##### Resources

* https://angularjs.org/
* https://docs.angularjs.org/
* http://ngmodules.org/
* http://www.encodedna.com/angularjs/tutorial/my-favorite-angularjs-features.htm
* http://code.tutsplus.com/tutorials/5-awesome-angularjs-features--net-25651

#### Bootstrap

* Responsive 

##### Bootstrap Resources

* http://getbootstrap.com/
* https://bootstrapbay.com/blog/reasons-to-use-bootstrap/

#### Bower & RequireJS

* Dependency Management for JavaScript Modules

### REST

* The REST user interface is the bridge between Inexor's HTML/JS user interface and Inexor's node.js application server
* We need some sort of two-way-data binding for the property tree

### Menus

We have two types of user interfaces: HUDs and menus

#### HUDS

* Mouse hidden
* May accept key input (console HUD)
* May not accept key input (score board HUD, game HUD)
* Doesn't accept mouse input / Mouse hidden
* Examples: console, score board, game states/ammo/flags, ...

#### Menus

* Mouse visible
* Accepts key input
* Accepts mouse input
* Examples: Main Menu, Multiplayer, Bot Match, Options, Texture Browser, ...

### Further development

* We will still need to do a lot of refactoring
* Implement the data exchange of the property tree:
 * Inexor HTML5 user interface --REST-->
  * Inexor node.js app server --protobuf-->
   * Inexor core game client
 * Inexor core game client --protobuf-->
  * Inexor node.js app server --REST-->
   * Inexor HTML5 user interface
* The console HUD needs easylogging to be merged into master
