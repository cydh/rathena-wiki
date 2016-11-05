---
title: Waitingroom2bg single
permalink: /Waitingroom2bg_single/
---

Syntax
------

-   [waitingroom2bg_single](/waitingroom2bg_single "wikilink")(<battle group>,"<mapname>",<x>,<y>,"<npc name>");

Description
-----------

Adds the first waiting player from the chat room of given [NPC](/NPC "wikilink") to an existing battleground group and warps it to specified coordinates on given map.

Examples
--------

`prontera,150,150,5 script  Test    99,{`
`   `[`end`](/end "wikilink")`;`
[`OnInit`](/OnInit "wikilink")`:`
`   `[`waitingroom`](/waitingroom "wikilink")` "BG Single",1,strnpcinfo(3)"::OnStart";`
`   `[`end`](/end "wikilink")`;`
`OnStart:`
`   `[`waitingroom2bg_single`](/waitingroom2bg_single "wikilink")`($@BGCroix,"bat_b01",150,150,strnpcinfo(3));`
`   end;`
`}`

[Category:Script_Command](/Category:Script_Command "wikilink") [Category:Battlegrounds_Command](/Category:Battlegrounds_Command "wikilink")