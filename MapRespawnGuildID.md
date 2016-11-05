---
title: MapRespawnGuildID
permalink: /MapRespawnGuildID/
---

Syntax
------

-   **maprespawnguildid** "<map name>",<guild id>,<flag>;

Description
-----------

This command goes through the specified map and for each player and monster found there does stuff.

Type Values
-----------

Flag is a bit-mask (add up numbers to get effects you want)

| Value | Description                                                                    |
|-------|--------------------------------------------------------------------------------|
| 1     | Warp all guild members to their save points.                                   |
| 2     | Warp all non-guild members (including guildless players) to their save points. |
| 4     | Remove all monsters which are not guardian or Emperium.                        |

Flag 7 will, therefore, mean 'wipe all mobs but guardians and the Emperium and kick all characters out', which is what the official scripts do upon castle surrender. Upon start of WoE, the scripts do 2 (warp all intruders out).

Example
-------

For examples, check the WoE scripts in the distribution.

[Category:Script Command](/Category:Script_Command "wikilink")