The new user interface requires a redesign of the keyboard and mouse handling.

## Keyboard input Handling

### Handling of key press and key release events (Binds)

Binds are managed in the C++ code and are handled in the current context (the layer which has the focus). Mouse keys and the mouse wheel are handled as normal keys also.

#### Bitmask

| Bit           | Layer         |
|:------------- |:------------- |
| Bit 0         | GameLayer     |
| Bit 1         | EditLayer     |
| Bit 2         | AppLayer      |
| Bit 3         | ChatLayer     |

#### Important binds / examples

| Key      | Action         | 0  | 1  | 2  | 3  | Remark              |
|:-------- |:-------------- |:-- |:-- |:-- |:-- |:------------------- |
| W        | Forward        | x  | x  |    |    |                     |
| A        | Left           | x  | x  |    |    |                     |
| S        | Backward       | x  | x  |    |    |                     |
| D        | Right          | x  | x  |    |    |                     |
| MOUSE 1  | Shot           | x  |    |    |    |                     |
| MOUSE 2  | WeaponChange   | x  |    |    |    |                     |
| ESC      | OpenAppLayer   | x  | x  |    |    | Open AppLayer, Change Location to main menu |
| ESC      | CloseAppLayer  |    |    | x  |    |                     |
| T        | OpenChatLayer  | x  | x  | x  |    |                     |
| ESC      | CloseChatLayer |    |    |    | x  |                     |
| F3       | OpenTextureBr. |    | x  |    |    | Open AppLayer, Change Location to texture browser |
| MWHEEL 1 | WeaponChange   | x  |    |    |    |                     |
| MWHEEL 2 | WeaponChange   | x  |    |    |    |                     |
| MWHEEL 1 |                |    | x  |    |    | Different actions in combination with other key modifiers |
| MWHEEL 2 |                |    | x  |    |    | Different actions in combination with other key modifiers |
| MWHEEL 1 | ScrollConsole  |    |    |    | x  | Scroll console up   |
| MWHEEL 2 | ScrollConsole  |    |    |    | x  | Scroll console down |

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

