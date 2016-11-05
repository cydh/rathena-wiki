---
title: Getmapusers
permalink: /Getmapusers/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   **getmapusers**("Map_Name");

Description
-----------

This function will return the number of users currently located on the specified map.

It is often used in the PVP scripts to check if a PVP room is full of not, if the number returned it equal to the maximum allowed it will not let you enter.

Example 1
---------

`//This will ask the player what map they want to check that has players and return the value`
`//of the players on the map`
[`input`](/input "wikilink")` @map$;`
[`mes`](/mes "wikilink")` `**`getmapusers`**`(@map$);`