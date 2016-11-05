---
title: OnPCLoadMapEvent
permalink: /OnPCLoadMapEvent/
---

Description
-----------

This special label will trigger once a player steps in a map marked with the **'loadevent**' [mapflag](/mapflag "wikilink") and attach its [RID](/RID "wikilink"). The fact that this label requires a [mapflag](/mapflag "wikilink") for it to work is because, otherwise, it would be server-wide and trigger every time a player would change maps.

Example
-------

`OnPCLoadMapEvent:`
`   getmapxy @map$,@x,@y,0;`
`   if (@map$ == "prontera") {`
`   sleep2 1000;`
`   getitem 601,1;`
`   }`
`   end;`

The script means that anyone who will go/warp to prontera, will receive item ID 601.