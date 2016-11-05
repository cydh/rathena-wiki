---
title: @warp Modification
permalink: /@warp_Modification/
---

In rAthena, warp system is meant for Game Masters by default. You can change this by heading over to your .../conf/[groups.conf](https://rathena.svn.sourceforge.net/svnroot/rathena/trunk/conf/groups.conf). What this guide is for is to help you put a message that says "Please click: Return to Save Point" when players are dead so that they can't use @go or @warp when they've died.

<h1>
Getting Started

</h1>
Lets get started. Head on over to .../src/map/atcommand.c and find:

`ACMD_FUNC(mapmove)`

Scroll down till you see this line:

`nullpo_retr(-1, sd);`
`    memset(map_name, '\0', sizeof(map_name));`

Add this code right after:

`if( pc_isdead(sd) ) {`
`   clif_displaymessage(fd, "Please click: Return to save point");`
`       return -1;`
`}`

So that it would look like this:

`{`
`   char map_name[MAP_NAME_LENGTH_EXT];`
`   unsigned short mapindex;`
`   short x = 0, y = 0;`
`   int m = -1;`
`   nullpo_retr(-1, sd);`
`   memset(map_name, '\0', sizeof(map_name));`
`   if( pc_isdead(sd) ) {`
`    clif_displaymessage(fd, "Please click: Return to Save Point");`
`   return -1;`
`   }`
`   if (!message || !*message ||`
`       (sscanf(message, "%15s %hd %hd", map_name, &x, &y) < 3 &&`
`        sscanf(message, "%15[^,],%hd,%hd", map_name, &x, &y) < 1)) {`
`        `
`           clif_displaymessage(fd, "Please, enter a map (usage: @warp/@rura/@mapmove `<mapname>` `<x>` `<y>`).");`
`           return -1;`
`   }`

As mentioned before, this modification makes it so that when a player tries to warp, they will get a message stating: "Please Click: Return To Save Point" instead of being warped.

<h1>
@go Portion

</h1>
Still in .../src/map/atcommand.c, find:

`{ MAP_ECLAGE,   110, 39 }, // 35=Eclage`

And then scroll down till you see this:

`memset(map_name, '\0', sizeof(map_name));`

And add this right after:

`if( pc_isdead(sd) ) {`
`  clif_displaymessage(fd, "Please click Return to save point");`
`      return -1;`
`}`

So that it would look like this:

`memset(map_name, '\0', sizeof(map_name));`
`if( pc_isdead(sd) ) {`
`  clif_displaymessage(fd, "Please click Return to save point");`
`      return -1;`
`}`
`memset(atcmd_output, '\0', sizeof(atcmd_output));`

[Category:Source Snippets](/Category:Source_Snippets "wikilink") [Category:Customization](/Category:Customization "wikilink")