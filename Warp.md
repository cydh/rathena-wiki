---
title: Warp
permalink: /Warp/
---

Syntax
------

-   **warp** &lt;"map name"&gt;, <x>, <y>;

Description
-----------

This command places (warps) the [currently attached](/RID#Usage "wikilink") player on given map, at given coordinates. Setting both *x* and *y* to 0 (zero) will cause the player get placed at a random spot. If the target cell is not walkable, it will cause an error and random placement. Parameter *map name* also accepts three magic names, where the *x* and *y* parameters are ignored: "Random" for random placement on current map, "Save" and "SavePoint" will warp the character to it's [save point](/save_point "wikilink").

Since warping causes all running scripts for the warped character to end, all commands that would normally be executed after warp, **will not get executed**, so there should not be any other command after warp, except [end](/end "wikilink").

Examples
--------

[`mes`](/mes "wikilink")` "OK, I'll warp you home now.";`
[`close2`](/close2 "wikilink")`;`
`warp "SavePoint", 0, 0;`
`end;`

Warps the player to his or her save point after closing the dialog.

`mes "Thank you for bringing me all";`
`mes "these things, but not get out.";`
[`next`](/next "wikilink")`;`
`warp "prontera", 150, 150;`
[`set`](/set "wikilink")` XYZQUEST,XYZQUEST|4;  // not executed`
`mes "See you.";           // not executed either`
[`close`](/close "wikilink")`;`

Will warp the player to Prontera at coordinates 150,150. Note, that anything past **warp** will not get executed (hidden bug, because quest progress is not updated).

[Category:Script Command](/Category:Script_Command "wikilink")