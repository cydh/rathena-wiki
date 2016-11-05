---
title: Setwall
permalink: /Setwall/
---

Syntax
------

-   **setwall** "<map name>",<x>,<y>,<size>,
    <dir>
    ,<shootable>,"<wallname>";

-   **delwall** "<wallname>";

Description
-----------

Creates an invisible wall, an array of "setcell" starting from x,y and doing a line of the given size in the given direction. The difference with setcell is this one updates the client part too, to avoid the glitch problem. Directions are the same as NPC sprite facing directions: 0=north, 1=northwest, 2=west, etc.

Examples
--------

`-  script  setwall -1,{`
`   `[`end`](/end "wikilink")`;`
[`OnInit`](/OnInit "wikilink")`:`
`   setwall "prontera",64,102,4,2,0,"PrtWall";`
`}`

------------------------------------------------------------------------

See Also
--------

-   [Delwall](/Delwall "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")