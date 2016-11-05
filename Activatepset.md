---
title: Activatepset
permalink: /Activatepset/
---

Syntax
------

-   **activatepset** <set number>;

Description
-----------

This command enables a previously defined for matching the public chat, against the patterns inside the set. This is required, when the set was previously disabled with [deactivatepset](/deactivatepset "wikilink") or newly created with [defpattern](/defpattern "wikilink").

Examples
--------

`prontera,150,150,0 script  Strange Spot    -1,{`
`    `[`mes`](/mes "wikilink")` "^808080You wonder, what this could be for...^00000";`
`    `[`close`](/close "wikilink")`;`
`OnHealPlayer:`
`    `[`percentheal`](/percentheal "wikilink")` 100, 100;`
`    `[`specialeffect2`](/specialeffect2 "wikilink")` EF_HEAL;`
`    `[`end`](/end "wikilink")`;`
`OnInit:`
`    `[`defpattern`](/defpattern "wikilink")` 1, "([^:]+):.*\\sheal plz(\\s.*)?", "OnHealPlayer";`
`    activatepset 1;`
`}`

This makes the NPC heal everyone in it's vicinity, who says "heal plz".

[Category:Script Command](/Category:Script_Command "wikilink")