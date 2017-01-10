## Component / System Overview

Component / System                | Language     | Description
--------------------------------- | ------------ | -----------
Inexor-Core                       | C/C++        | Game-State, Rendering and calculate anything performance sensitive
Inexor-GlueGen                    | C/C++        | External application used in the build-process to generate our networking code (and potentially other glue code)
[Inexor-Flex](/inexor-game/flex/) | JS (NodeJS)  | Provides a scripting environment for the server and client, provides the Inexor-User-Interface
Inexor-UI-HUD                     | HTML5+JS+CSS | The Inexor UI HUD is basically a website, which is rendered by the Inexor-Core
Inexor-UI-APP                     | HTML5+JS+CSS | The Inexor UI APP is basically a website, which is rendered by the Inexor-Core

### Component / System Interoperability

Component / System                | Connection                  | Component / System
--------------------------------- | --------------------------- | -----------
Inexor-Core                       | Inexor Tree [using gRPC](/inexor-game/code/wiki/RPC-Node.js)  | Inexor-Flex
Inexor-Flex                       | [[Inexor Tree]] using REST  | Inexor-UI-HUD
Inexor-Flex                       | [[Inexor Tree]] using REST  | Inexor-UI-APP
Inexor-Flex                       | [[Inexor Tree]] using REST  | Inexor-Flex (remote)
Inexor-Core                       | Key Events using CEF-RPC    | Inexor-UI-APP (only APP, not HUD!)

### Components / Systems

#### Inexor Core

* Game State
  * Physics
  * World
  * ...
* Graphics
  * Rendering Game-Graphics
  * Rendering the Inexor-UI-HUD
  * Rendering the Inexor-UI-APP
* Input Handling
  * Mouse
  * Keyboard
  * Forwarding key events to the Inexor-User-Interface

#### Inexor Flex

* Webserver
  * Provides [[Inexor Tree]] REST API
  * Provides Inexor-UI-APP (HTML5/JS/CSS webapplication)
  * Provides Inexor-UI-HUD (HTML5/JS/CSS webapplication)
* Business Logic
  * Texture-Manager
  * Map-Manager
  * Media-Manager (Music, Sound, Videos)
  * Server-List-Manager
  * ...

#### Inexor-UI-APP

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

#### Inexor-UI-HUD

* The ingame HUD for the Inexor Core (Client)
* Small web application written in HTML5/JS/CSS
* Loads data from the [[Inexor Tree]] REST API
