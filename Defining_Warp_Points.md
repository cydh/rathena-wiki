---
title: Defining Warp Points
permalink: /Defining_Warp_Points/
---

These kind of [scripts](/Scripting "wikilink") are used to show a warp in-game and define where to warp a player.

Basic syntax
------------

<from map name>`,`<fromX>`,`<fromY>`,`<facing>`(tab)warp(tab)`<warp name>`(tab)`<spanx>`,`<spany>`,`<to map name>`,`<toX>`,`<toY>

**From map name**, **fromX** and **fromY** defines where the warp will be placed. **facing** is not irrelevant so you can set it to zero.

**warp name** declares the warp's name so you can enable or disable it using @enablenpc or @disablenpc atcommands.

SpanX and SpanY will make the warp sensitive to a character who didn't step directly on it, but walked into a zone which is centered on the warp from coordinates and is SpanX in each direction across the X axis and SpanY in each direction across the Y axis.

So here is an example how our warp must look:

`prontera,107,215,0 warp    prt01   2,2,prt_in,240,139`

When we have completed defining our warp, we can add it to a existing warp file (placed in folder) or create a new file. If you choose the last don't forget to [add the new file to script list](/Adding_Script "wikilink")!

[Category:Scripting](/Category:Scripting "wikilink")