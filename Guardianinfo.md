---
title: Guardianinfo
permalink: /Guardianinfo/
---

Syntax
------

**guardianinfo**("<map name>", <guardian number>, <type>);

Description
-----------

This function will return various info about the specified guardian, or -1 if it fails for some reason. It is primarily used in the castle manager NPC.

Map name and guardian number (value between 0 and 7) define the target. Type indicates what information to return:

`0 - visibility (whether the guardian is installed or not)`
`1 - max. hp`
`2 - current hp`

Examples
--------

From

`mes "["+`[`strnpcinfo`](/strnpcinfo "wikilink")`(1)+"]";`
`   mes "Will you summon a Guardian? It'll be a protector to defend us loyally.";`
`   mes "Please select a guardian to defend us.";`
`   `[`next`](/next "wikilink")`;`
`   `[`for`](/for "wikilink")`( set .@i, 0; .@i <= 7 ; set .@i, .@i+1 ) {`
`       `[`if`](/if "wikilink")` (.@guardiantype[.@i] == 1) { `[`set`](/set "wikilink")` .@type$,"Guardian Soldier"; }`
`       `[`else` `if`](/else_if "wikilink")` (.@guardiantype[.@i] == 2) { set .@type$,"Guardian Archer"; }`
`       `[`else`](/else "wikilink")` { set .@type$,"Guardian Knight"; }`
`       if (`**`guardianinfo`**`(`[`strnpcinfo`](/strnpcinfo "wikilink")`(2),.@i,0)) {`
`           `[`setarray`](/setarray "wikilink")` .@gname$[.@i], .@type$ + " - Implemented (" + `**`guardianinfo`**`(`[`strnpcinfo`](/strnpcinfo "wikilink")`(2),.@i,2) + "/" + `**`guardianinfo`**`(`[`strnpcinfo`](/strnpcinfo "wikilink")`(2),.@i,1) + ")";`
`       }`
`       else {`
`           `[`setarray`](/setarray "wikilink")` .@gname$[.@i], .@type$ + " - Not Implemented";`
`       }`
`   }`

In this code, [strnpcinfo](/strnpcinfo "wikilink")(2) is the hidden part of the NPC's display name e.g Guardian\#*archer1*

[Category:Script Command](/Category:Script_Command "wikilink")