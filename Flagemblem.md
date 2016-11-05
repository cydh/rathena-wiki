---
title: Flagemblem
permalink: /Flagemblem/
---

Syntax
------

-   **flagemblem** <guild id>;

Description
-----------

This command only works when run by the [NPC](/NPC "wikilink") objects which have sprite id 722, which is a 3D guild flag sprite. If it isn't, the data will change, but nothing will be seen by anyone. If it is invoked in that manner, the emblem of the specified guild will appear on the flag, though, if any players are watching it at this moment, they will not see the emblem change until they move out of sight of the flag and return.

This is commonly used in official guildwar scripts with a function call which returns a guild id.

Examples
--------

`   // This will change the emblem on the flag to that of the guild that owns`
`   // "guildcastle"`
`   `**`flagemblem`**` `[`GetCastleData`](/GetCastleData "wikilink")`("guildcastle",1); `

[Category:Script_Command](/Category:Script_Command "wikilink")