---
title: Areawarp
permalink: /Areawarp/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [areawarp](/areawarp "wikilink") "from_mapname",<x1>,<y1>,<x2>,<y2>,"to_mapname",<x3>,<y3>;

Description
-----------

This command is similar to '[warp](/warp "wikilink")', however, it will not refer to the invoking character, but instead, all characters within a specified area, defined by the x1/y1-x2/y2 square, will be warped. Nobody outside the area will be affected, including the activating character, if they are outside the area.

Examples
--------

    areawarp "place",10,10,120,120,"place2",150,150;

Everyone that is in the area between X 10 Y 10 and X 120 Y 120, in a square shape, on the map called "place", will be affected, and warped to "place2" X 150 Y 150

    areawarp "place",10,10,120,120,"place2",0,0;

By using ,0,0; as the destination coordinates it will take all the characters in the affected area to a random set of co-ordinates on "place2".

Like '[warp](/warp "wikilink")', areawarp will also explicitly warp characters randomly into the current map if you give the 'to map name' as "Random".