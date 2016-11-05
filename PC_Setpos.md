---
title: PC Setpos
permalink: /PC_Setpos/
---

Syntax
------

`int `**`pc_setpos`**`(struct map_session_data* sd, unsigned short mapindex, int x, int y, uint8 clrtype);`

Parameters
----------

| Parameter    | Description                                                                     |
|--------------|---------------------------------------------------------------------------------|
| **sd**       | Session data of the player to move.                                             |
| **mapindex** | Map index of the target map.                                                    |
| **x**        | X-coordinate on the target map.                                                 |
| **y**        | Y-coordinate on the target map.                                                 |
| **clrtype**  | Visual effect upon removing the player from it's current position (clear type).

                -   0 - Character fades out.
                -   1 - Character will be displayed as dead.
                -   2 - Re-spawn animation.
                -   3 - Teleport animation.                                                      |

Description
-----------

Changes position of a player to a given map and coordinates. If the target map is on different server, it will forward the client to it. If x and y are 0 (zero), random coordinates will be chosen.

Example
-------

`pc_setpos(sd, mapindex_name2id(MAP_PAYON), 0, 0, 0);`

Warps the player *sd* to payon on random coordinates without a warp-out effect. Note, that MAP_PAYON is a source define, which resolves to "payon".

[Category:Source Functions](/Category:Source_Functions "wikilink")