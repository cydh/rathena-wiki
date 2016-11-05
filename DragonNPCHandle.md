---
title: DragonNPCHandle
permalink: /DragonNPCHandle/
---

Rune Knight Dragon : NPC Handle
===============================

This page is a short explanation of the available functions to handle **RK Dragons**

### checkdragon()

Allows you to check if the player is mounting a dragon. Example below

`if( checkdragon() )`
`   dispbottom "You are mounting!";`
`else`
`   dispbottom "You are not mounting";`

### setdragon({optional Color})

Allows you to set a player to mount a dragon with a color of your choice.
It's only param **Color** allows you to set which of the color the dragon will be, there are 5 options

-   1 : Green Dragon
-   2 : Brown Dragon
-   3 : Gray Dragon
-   4 : Blue Dragon
-   5 : Red Dragon

When color is *not provided* the green dragon will be used, below is an **Example** with conjunction of *checkdragon()*

`if( checkdragon() ) {`
`   mes "You are already mounting";`
`   close;`
`} else {`
`   mes "Select the color of your dragon";`
`   set .@choice,select("Green Dragon","Brown Dragon","Gray Dragon","Blue Dragon","Red Dragon");`
`   //Notice we pass the number of the chosen menu to setdragon so it picks the color the user wants`
`   setdragon(.@choice);`
`}`

Changelog
---------

-   [r15009](http://sourceforge.net/apps/trac/rathena/changeset/15009) Added from RREMu.

[Category:Script Command](/Category:Script_Command "wikilink")