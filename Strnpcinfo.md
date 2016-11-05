---
title: Strnpcinfo
permalink: /Strnpcinfo/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [strnpcinfo](/strnpcinfo "wikilink")(<type>);

Description
-----------

This function will return the various parts of the name of the calling [NPC](/NPC "wikilink"). Whatever it returns is determined by type.

Type Values
-----------

| Value | Description                                 |
|-------|---------------------------------------------|
| 0     | The NPC's display name (visible\#hidden).   |
| 1     | The visible part of the NPC's display name. |
| 2     | The hidden part of the NPC's display name   |
| 3     | The NPC's unique name (::name).             |
| 4     | The name of the map the NPC is in.          |

Examples
--------

`monk_test,306,151,5    script  Sealed Shrine#1::SS_1   111,{`
`   `[`mes`](/mes "wikilink")` `**`strnpcinfo`**`(0); // Sealed Shrine#1`
`   mes strnpcinfo(1); // Sealed Shrine`
`   mes strnpcinfo(2); // 1`
`   mes strnpcinfo(3); // SS_1`
`   mes strnpcinfo(4); // monk_test`
`   `[`close`](/close "wikilink")`;`
`}`