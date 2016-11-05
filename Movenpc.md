---
title: Movenpc
permalink: /Movenpc/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [movenpc](/movenpc "wikilink") <NPC name>,x,y;

Description
-----------

This command looks like the NPCWalkToxy function, but is a little different.

While NPCWalkToXY just makes the NPC 'walk' to the coordinates given (which sometimes gives problems if the path isn't a straight line without objects), this command just moves the NPC. It basically warps out and in on the current and given spot.

Examples
--------

`// This will move Bugga from it's current position to the`
`// coords 100,20 (if those coords are walkable (legit)).`
`movenpc "Bugga",100,20;`