---
title: Break
permalink: /Break/
---

Syntax
------

-   [break](/break "wikilink");

Description
-----------

This command lets you break out of a [loop](/Loops#Break_and_Continue "wikilink") or a [switch](/switch "wikilink") block. After the break; command has been issued, the script will continue where needed.

Examples
--------

[`switch`](/switch "wikilink")` (`[`getequipweaponlv`](/getequipweaponlv "wikilink")`(EQI_HAND_L)) {`
[`case`](/case "wikilink")` 0:`
`   `[`mes`](/mes "wikilink")` "You are holding a shield, so it doesnt have a level";`
`   `[`break`](/break "wikilink")`;`
[`case`](/case "wikilink")` 1:`
`case 2:`
`case 3:`
`case 4:`
`   `[`mes`](/mes "wikilink")` "You are holding a lvl "+ `[`getequipweaponlv`](/getequipweaponlv "wikilink")`(EQI_HAND_L) +" weapon";`
`   `[`break`](/break "wikilink")`;`
[`case`](/case "wikilink")` 5:`
`   `[`mes`](/mes "wikilink")` "You are holding a lvl 5 weapon, hm, must be a custom design";`
`   `[`break`](/break "wikilink")`;`
`}`
[`close`](/close "wikilink")`;`

See Also
--------

-   [Loops\#Break_and_Continue](/Loops#Break_and_Continue "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")