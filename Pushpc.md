---
title: Pushpc
permalink: /Pushpc/
---

Syntax
------

-   [pushpc](/pushpc "wikilink") <direction>,<cells>;

Description
-----------

This command will push the [currently attached player](/RID "wikilink") to given direction by given amount of square cells. Direction is the same as used when declaring NPCs, and can be specified by using one of the DIR_\* constants

The knock-back is not restricted by items or map flags, only obstacles are taken into account. If there is not enough space to perform the push (e.g. due to a wall), the character is pushed only up to the obstacle.

Examples
--------

`// pushes the character 5 cells in 3 o'clock direction from it's current position.`
`pushpc DIR_EAST, 5;`

[Category:Script Command](/Category:Script_Command "wikilink")