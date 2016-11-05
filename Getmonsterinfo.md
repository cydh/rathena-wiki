---
title: Getmonsterinfo
permalink: /Getmonsterinfo/
---

Syntax
------

-   [getmonsterinfo](/getmonsterinfo "wikilink")(<mob ID>,<type>)

Description
-----------

This function will look up the monster with the specified ID number in the mob database and return the info set by TYPE argument.

Valid types are listed in :

-   0 = Monster Name
-   1 = Monster Level
-   2 = Monster Max HP
-   3 = Monster Base EXP
-   4 = Monster Job EXP
-   5 = Monster Attack 1
-   6 = Monster Attack 2
-   7 = Monster Defend
-   8 = Monster MDef
-   9 = Monster STR
-   10 = Monster AGI
-   11 = Monster VIT
-   12 = Monster INT
-   13 = Monster DEX
-   14 = Monster LUK
-   15 = Monster Range1
-   16 = Monster Range2
-   17 = Monster Range3
-   18 = Monster Size
-   19 = Monster Race
-   20 = Monster Element
-   21 = Monster Mode
-   22 = Monster MVP EXP

It will return -1 if there is no such monster (or the type value is invalid), or "null" if you requested the monster's name.

Examples
--------

[Category:Script Command](/Category:Script_Command "wikilink")