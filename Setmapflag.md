---
title: Setmapflag
permalink: /Setmapflag/
---

Syntax
------

-   [setmapflag](/setmapflag "wikilink") "<map name>",<flag>{,<zone>};

Description
-----------

This command marks a specified map with a map flag given. Map flags alter the behavior of the map, you can see the list of the available ones in '' under 'mf_'.

The map flags alter the behavior of the map regarding teleporting (mf_nomemo, mf_noteleport, mf_nowarp, mf_nogo), storing location when disconnected (mf_nosave), dead branch usage (mf_nobranch), penalties upon death (mf_nopenalty, mf_nozenypenalty), PVP behavior (mf_pvp, mf_pvp_noparty, mf_pvp_noguild), WoE behavior (mf_gvg,mf_gvg_noparty), ability to use skills or open up trade deals (mf_notrade, mf_novending, mf_noskill, mf_noicewall), current weather effects (mf_snow, mf_fog, mf_sakura, mf_leaves, mf_rain, mf_clouds, mf_fireworks) and whether night will be in effect on this map (mf_nightenabled).

The zone optional parameter is used to set the zone for restricted mapflags.

Examples
--------

`// This sets the 'novending' mapflag on Prontera`
`setmapflag "prontera", mf_novending;`

See Also
--------

-   [mapflag](/mapflag "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")