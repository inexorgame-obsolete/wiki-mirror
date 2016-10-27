The new user interface requires a redesign of the keyboard and mouse handling.

## Keyboard input Handling

### Handling of key press and key release events (Binds)

Binds are managed in the C++ code. The mouse buttons and the mouse wheel are handled as normal keys also.

#### Bit mask

The bit mask describes for which layers are affected by the key bind. The bits can be combined which means a bind affects multiple layers. If a key is pressed, it is checked if the bind affects the current layer.

| Bit           | Layer         |
|:------------- |:------------- |
| Bit 0         | GameLayer     |
| Bit 1         | EditLayer     |
| Bit 2         | AppLayer      |
| Bit 3         | ChatLayer     |

#### Bind mask

It shouldn't be able to bind all keys on all layers. In order to prevent useless or conflicting key/bitmask bindings, we're using a bind mask like shown in the table below. The X indicates if a key can be bind with the given bit.

| Key           | 0  | 1  | 2  | 3  |
|:------------- |:-- |:-- |:-- |:-- |
| A-Z           | x  | x  |    |    |
| a-z           | x  | x  |    |    |
| 0-9           | x  | x  |    |    |
| !"§$%&/()=?   | x  | x  |    |    |
| ENTER         | x  | x  |    |    |
| POS1,END      | x  | x  |    |    |
| BACKSPACE,DEL | x  | x  |    |    |
| MOUSEWHEEL1-2 | x  | x  | x  | x  |
| MOUSE1-3      | x  | x  | x  | x  |
| ESC           | x  | x  | x  | x  |
| F1-F12        | x  | x  | x  | x  |

#### Important binds / examples

| Key      | Action         | 0  | 1  | 2  | 3  | Remark                                                    |
|:-------- |:-------------- |:-- |:-- |:-- |:-- |:--------------------------------------------------------- |
| W        | Forward        | x  | x  |    |    |                                                           |
| A        | Left           | x  | x  |    |    |                                                           |
| S        | Backward       | x  | x  |    |    |                                                           |
| D        | Right          | x  | x  |    |    |                                                           |
| MOUSE 1  | Shot           | x  |    |    |    |                                                           |
| MOUSE 2  | WeaponChange   | x  |    |    |    |                                                           |
| ESC      | OpenAppLayer   | x  | x  |    |    | Open AppLayer, Change location to main menu               |
| ESC      | CloseAppLayer  |    |    | x  |    |                                                           |
| T        | OpenChatLayer  | x  | x  | x  |    |                                                           |
| ESC      | CloseChatLayer |    |    |    | x  |                                                           |
| F1       | OpenServerBr.  | x  |    |    |    | Open AppLayer, Change location to server browser          |
| F3       | OpenTextureBr. |    | x  |    |    | Open AppLayer, Change location to texture browser         |
| F4       | OpenModelBr.   |    | x  |    |    | Open AppLayer, Change location to model browser           |
| MWHEEL 1 | WeaponChange   | x  |    |    |    |                                                           |
| MWHEEL 2 | WeaponChange   | x  |    |    |    |                                                           |
| MWHEEL 1 |                |    | x  |    |    | Different actions in combination with other key modifiers |
| MWHEEL 2 |                |    | x  |    |    | Different actions in combination with other key modifiers |
| MWHEEL 1 | ScrollConsole  |    |    |    | x  | Scroll console up                                         |
| MWHEEL 2 | ScrollConsole  |    |    |    | x  | Scroll console down                                       |


### Handling of text input

If no bind (key+bitmask) has matched, the key input is handled as text input. Text input is forwarded to the target layer as shown in the table below:

| GameLayer | EditLayer | AppLayer | ChatLayer | Target        |
|:--------- |:--------- |:-------- |:--------- |:------------- |
| active    | inactive  | inactive | inactive  | Ignore        |
| inactive  | active    | inactive | inactive  | Ignore        |
| *         | *         | active   | inactive  | AppLayer      |
| *         | *         | *        | active    | ChatLayer     |

## Mouse input handling

If no bind (key+bitmask) has matched, the key input is handled as text input. Text input is forwarded to the target layer as shown in the table below:

| Mouse input      | GameLayer | EditLayer | AppLayer | ChatLayer | Target        | Remarks                  |
|:---------------- |:--------- |:--------- |:-------- |:--------- |:------------- |:------------------------ |
| Mouse X / Y      | *         | *         | inactive | inactive  | GameLayer     | Rotates the player       |
| Mouse X / Y      | *         | *         | active   | inactive  | AppLayer      | Move the mouse in the UI |
| Mouse X / Y      | *         | *         | *        | active    | Ignore        | No mouse input in chat   |
| Mousewheel U / D | active    | inactive  | inactive | inactive  | GameLayer     | Binds                    |
| Mousewheel U / D | *         | active    | inactive | inactive  | EditLayer     | Binds                    |
| Mousewheel U / D | *         | *         | active   | inactive  | AppLayer      | Mouse wheel in the UI    |
| Mousewheel U / D | *         | *         | *        | active    | ChatLayer     | Binds                    |

