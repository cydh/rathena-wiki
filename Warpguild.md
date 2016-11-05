---
title: Warpguild
permalink: /Warpguild/
---

Syntax
------

-   [warpguild](/warpguild "wikilink") "<mapname>",<x>,<y>,<guild_id>;

Description
-----------

Warps a guild to specified map and coordinate given the guild id, which you can get with [getcharid](/getcharid "wikilink")(2). You can also request another guild id given the member's name with [getcharid](/getcharid "wikilink")(2,<player_name>).

You can use the following "map names" for special warping behavior:

Random
All party members are randomly warped in their current map (as if they all used a fly wing)

SavePointAll
All party members are warped to their respective save point.

SavePoint
All party members are warped to the save point of the currently attached player (will fail if there's no player attached).

Example
-------

`warpguild "prontera",x,y,Guild_ID;`

[Category:Script Command](/Category:Script_Command "wikilink")