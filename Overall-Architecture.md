## Component / System Overview

Component / System  | Repository                             | Language     | Description
------------------- | -------------------------------------- | ------------ | -----------
[[Inexor Core]]     | [code](/inexor-game/flex/)             | C/C++        | Game-State, Rendering and calculate anything performance sensitive
[[Inexor GlueGen]]  | [code](/inexor-game/code/)             | C/C++        | External application used in the build-process to generate our networking code (and potentially other glue code)
[[Inexor Flex]]     | [flex](/inexor-game/flex/)             | JS (NodeJS)  | Provides a scripting environment for the server and client, provides the Inexor User Interfaces
Inexor UI HUD       | [interfaces](/inexor-game/interfaces/) | HTML5+JS+CSS | The Inexor UI HUD is basically a website, which is rendered by the Inexor Core
Inexor UI APP       | [interfaces](/inexor-game/interfaces/) | HTML5+JS+CSS | The Inexor UI APP is basically a website, which is rendered by the Inexor Core

### Component / System Interoperability

Component / System                | Connection                  | Component / System
--------------------------------- | --------------------------- | -----------
[[Inexor Core]]                   | Inexor Tree [using gRPC](/inexor-game/code/wiki/RPC-Node.js)  | Inexor-Flex
[[Inexor Flex]]                   | [[Inexor Tree]] using REST  | Inexor-UI-HUD
[[Inexor Flex]]                   | [[Inexor Tree]] using REST  | Inexor-UI-APP
[[Inexor Flex]]                   | [[Inexor Tree]] using REST  | [[Inexor Flex]] (remote)
Inexor-Core                       | Key Events using CEF-RPC    | Inexor-UI-APP (only APP, not HUD!)

### Components / Systems

#### Inexor Core

Component / System                | Topic                  | Sub Topic                    | Sub Sub Topic
--------------------------------- | ---------------------- | ---------------------------- | ----------
[[Inexor Core]]                   | Game State             | Physics                      | 
                                  |                        | World                        | 
                                  |                        | Player                       | 
                                  | Graphics               | Rendering Game-Graphics      | Octree
                                  |                        |                              | Textures
                                  |                        |                              | Models
                                  |                        |                              | Entities
                                  |                        |                              | Particles
                                  |                        | Rendering HTML5 Applications | Inexor-UI-HUD
                                  |                        |                              | Inexor-UI-APP
                                  | Input                  | Game Movement                | Mouse
                                  |                        |                              | Keyboard
                                  |                        |                              | Key Bindings
                                  |                        | UI Input Handling            | Mouse Events
                                  |                        |                              | Key Events

#### Inexor Flex

* Webserver
  * Provides [[Inexor Tree]] REST API
  * Provides multiple web applications
* Web applications (HTML5/JS/CSS)
  * Inexor Flex User Interface
  * Inexor Core (Client) Menu & Application
  * Inexor Core (Client) HUD
  * Inexor Core (Server) User Interface
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
