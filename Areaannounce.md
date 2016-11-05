---
title: Areaannounce
permalink: /Areaannounce/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [areaannounce](/areaannounce "wikilink") "mapname",<x1>,<y1>,<x2>,<y2>,"Message",<flag>{,<color>};

Description
-----------

This command works like '[announce](/announce "wikilink")' but will only broadcast to characters residing in the specified x1/y1-x2/y2 square on the map given. The flags and color parameter given are the same as in '[announce](/announce "wikilink")', but only the color related ones have effect.

Examples
--------

    areaannounce "prt_church",0,0,350,350,"God's in his heaven, all right with the world",0;