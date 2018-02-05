Branches | Issues | Main developers
-------- | ------ | ---
[ogro/conquer_world](/inexorgame/code/tree/ogro/conqueror_world), [inky/killing_spree](/inexorgame/code/tree/inky/killing_spree) | [#6](/inexorgame/code/issues/6), [#7](/inexorgame/code/issues/7) | [@inexorgame](/inexorgame)

See also:
* [[Gamemodes]]
* [[Weapon System]]
* [[Map Creator: Visual Scripting]]

## The idea:

We can separate the things needed for a game mode into two parts:
- generic logic
    - round limit (time/points), which weapons to enable, ..
- special logic
    - "if i stay near the entity `flag` it makes me `flagholder`"
    - "if i am `flagholder` and stay near `own flag` and near `own basespot`, I score"

Now the **generic logic** is easy to handle:  
Just hardcode the logic how to set a "round limit" in C++ or JavaScript.
Then just distribute the variable "round limit" to everyone.  
-> Safe: not sharing a potentially malicious "gamemode-script". Instead you share a "gamemode-settings.toml" with  "round limit" set to a constant. That file is just static data, no harm can come from here.

The **special logic** is harder to handle:  
You need some a set of [Lego](https://en.wikipedia.org/wiki/Lego)-bricks, which are each on their own not able to do harm.
With other words: You want to have a safe subset of a scripting "language" here.

The most promising idea is to currently create a Scripting Sandbox inside the Map Creator:  
People can build their scripts like they do in Minecraft, by building them together with materials.

The system we propose is a bit different though: [[Map Creator: Visual Scripting]]