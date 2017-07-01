In contrast to the cube2 engine Inexor uses standard web technologies for user interfaces. This means the user interfaces are implemented using HTML5+, CSS3+ and JavaScript.

By super-seeding the self-implementation we introduce a lot of massive changes. This wiki page describes the function of the overall system.

### The `Inexor Core` game client

The `Inexor Core` game client uses the Chromium Embedded Framework (short: `CEF`) for rendering websites. The rendering happens in separate processes which is important for the performance of the game. Rendering the websites doesn't affect the main process of game.

A website is rendered on a transparent texture layer in front of the game. As `CEF` writes directly on the texture in the gfx memory the Inexor Core game client only has to blend the texture. This makes the user interface having a very low impact on the performance.

Furthermore the `Inexor Core` game client can handle multiple user interfaces. Each has user interface is rendered on a separate transparent texture. We call this method `layers` because we can show or hide an user interface or rearrange their order of appearance.

### `Inexor Flex`

Someone have to deliver the websites shown in the `Inexor Core` game client. The is handled by `Inexor Flex`. Flex is able to provide multiple user interfaces at the same time.

Furthermore Inexor Flex not only provides user interfaces shown in the `Inexor Core` game client. It provides also user interfaces for the `Inexor Core` game server or for managing Inexor Flex itself.

The Inexor project provides the following user interfaces:

| User Interface | Ingame | Description |
| --- | --- | --- |
| [ui-flex](/inexorgame/ui-flex) | <ul><li>[ ] Ingame</li><li>[x] Standalone</li></ul> | Management of instances, media repositories, user interfaces, logging and updating Inexor |
| [ui-client-hud](/inexorgame/ui-client-hud) | <ul><li>[x] Ingame</li><li>[ ] Standalone</li></ul> | Ingame HUD |
| [ui-client-interface](/inexorgame/ui-client-interface) | <ul><li>[x] Ingame</li><li>[ ] Standalone</li></ul> | Ingame dialogs like settings |
| [ui-console](/inexorgame/ui-console) | <ul><li>[x] Ingame</li><li>[x] Standalone</li></ul> | The console prints text messages (chat or command output) and allows to input commands. The console is used in the game client but also in a web browser for managing game servers |
 
It's possible to extend Inexor to provide own user interfaces. Here are some ideas:

| User Interface | Description |
| --- | --- |
| Server Admin Panel | A server owner can provide an additional user interface for the management of the server |
| Clan/Community | The game client shows information about your mates |
| Editing UI |  |
| Map generation UI |  |
