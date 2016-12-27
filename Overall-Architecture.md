## Component / System Overview

Component / System                | Language     | Description
--------------------------------- | ------------ | -----------
Inexor-Kernel                     | C/C++        | Game-State, Rendering and calculate anything performance sensitive
Inexor-GlueGen                    | C/C++        | External application used in the build-process to generate our networking code (and potentially other glue code)
[Inexor-Flex](/inexor-game/flex/) | JS (NodeJS)  | Provides a scripting environment for the server and client, provides the Inexor-User-Interface
Inexor-User-Interface             | HTML5+JS+CSS | The user interface is basically a website, which is rendered by the Inexor-Kernel

### Component / System Interoperability

Component / System                | Connection                  | Component / System
--------------------------------- | --------------------------- | -----------
Inexor-Kernel                     | Inexor Tree [using gRPC](/inexor-game/code/wiki/RPC-Node.js)  | Inexor-Flex
[Inexor-Flex](/inexor-game/flex/) | [[Inexor Tree]] using REST  | Inexor-User-Interface
Inexor-Kernel                     | Key Events using CEF-RPC    | Inexor-User-Interface

### Components / Systems

#### Inexor Kernel

* Game State
  * Physics
  * World
  * ...
* Graphics
  * Rendering Game-Graphics
  * Rendering Inexor-User-Interface
* Input Handling
  * Mouse
  * Keyboard
  * Forwarding key events to the Inexor-User-Interface

#### Inexor Flex

* Webserver
  * Provides [[Inexor Tree]] REST API
  * Provides Inexor-User-Interface (HTML5/JS/CSS webapplication)
  * Provides Inexor-Game-HUD (HTML5/JS/CSS webapplication)
* Business Logic
  * Texture-Manager
  * Map-Manager
  * Media-Manager (Music, Sound, Videos)
  * Server-List-Manager
  * ...

#### Inexor-User-Interface

* Modular Single-Page-Webapplication written using web standards (HTML5/JS/CSS).
* Loads data from the [[Inexor Tree]] REST API
* User Interface
  * Menus
  * Frontend for the Business Logic in Inexor-Flex

Inexor-User-Interface | Inexor-Flex Business Logic Component
--------------------- | ------------------------------------
Texture-Browser       | Texture-Manager
Map-Chooser           | Map-Manager
Media-Player          | Media-Manager

