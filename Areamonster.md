---
title: Areamonster
permalink: /Areamonster/
---

Syntax
------

-   [areamonster](/areamonster "wikilink") &lt;"map name"&gt;, <x1>, <y1>, <x2>, <y2>, &lt;"display name"&gt;, <mob id>, <amount>\[, &lt;"event label"&gt;\];

Description
-----------

This command works exactly same as [monster](/monster "wikilink"), with the exception, that an area can be specified, in which a monster, or more often multiple monsters, are randomly distributed, rather than a single coordinate.

Parameters *x1* and *y1* specify the lower left corner of the bounding rectangle, and *x2* and *y2* the upper right one. For example specifying a rectangle of 2, 3, 5, 7, will spawn the monsters inside an 4x5 cell area, as illustrated below:

`7--XXXX`
`6  XXXX`
`5  XXXX`
`4  XXXX`
`3--XXXX`
`2  |  |`
`1  |  |`
`0  |  |`
` 01234567`

Examples
--------

`   `[`mes`](/mes "wikilink")` "Did the Porings die again?";`
`   `[`mes`](/mes "wikilink")` "OK, I'll repair the Poring garden.";`
`   `[`close2`](/close2 "wikilink")`;`
`   `[`areamonster`](/areamonster "wikilink")` "this", 213, 110, 233, 140, "Garden Poring", 1002, 20, strnpcinfo(0)+"::OnKilled";`
`   `[`end`](/end "wikilink")`;`
`OnKilled:`
`   `[`mes`](/mes "wikilink")` "Do not kill these precious Porings!";`
`   `[`close`](/close "wikilink")`;`

This populates an area considered as an Poring Garden with 20 Porings. If one of them is killed, the killer is told not to kill them.

[Category:Script Command](/Category:Script_Command "wikilink")