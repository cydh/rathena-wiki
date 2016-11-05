---
title: Getequipweaponlv
permalink: /Getequipweaponlv/
---

Syntax
------

-   [getequipweaponlv](/getequipweaponlv "wikilink")(<equipment slot>)

Description
-----------

This function returns the weapon level for the weapon equipped in the specified equipment slot on the invoking character. For a list of equipment slots see '[getequipid](/getequipid "wikilink")'.

Only EQI_HAND_L and EQI_HAND_R normally make sense, since only weapons have a weapon level. You can, however, probably, use this field for other equippable custom items as a flag or something. If no item is equipped in this slot, or if it doesn't have a weapon level according to the database, 0 will be returned.

Examples
--------

[`switch`](/switch "wikilink")` (`[`getequipweaponlv`](/getequipweaponlv "wikilink")`(EQI_HAND_R)) {`
[`case`](/case "wikilink")` 1:`
`   `[`mes`](/mes "wikilink")` "You are holding a lvl 1 weapon";`
`   `[`break`](/break "wikilink")`;`
`case 2:`
`   mes "You are holding a lvl 2 weapon";`
`   break;`
`case 3:`
`   mes "You are holding a lvl 3 weapon";`
`   break;`
`case 4:`
`   mes "You are holding a lvl 4 weapon";`
`   break;`
`case 5:`
`   mes "You are holding a lvl 5 weapon, hm, must be a custom design";`
`   break;`
`default:`
`   mes "Seems you don't have a weapon on";`
`   break;`
`}`

Or for the left hand, cause it can hold a weapon or a shield:

`   `[`if`](/if "wikilink")`(`[`getequipid`](/getequipid "wikilink")`(EQI_HAND_R)==0) `[`goto`](/goto "wikilink")` L_NothingEquiped;`
`   switch (getequipweaponlv(EQI_HAND_L)) {`
`   `[`case`](/case "wikilink")` 0:`
`       `[`mes`](/mes "wikilink")` "You are holding a shield, so it doesnt have a level";`
`       `[`break`](/break "wikilink")`;`
`   case 1:`
`       mes "You are holding a lvl 1 weapon";`
`       break;`
`   case 2:`
`       mes "You are holding a lvl 2 weapon";`
`       break;`
`   case 3:`
`       mes "You are holding a lvl 3 weapon";`
`       break;`
`   case 4:`
`       mes "You are holding a lvl 4 weapon";`
`       break;`
`   case 5:`
`       mes "You are holding a lvl 5 weapon, hm, must be a custom design";`
`       break;`
`   }`
`   `[`close`](/close "wikilink")`;`
`L_NothingEquiped:`
`   mes "Seems you have nothing equipped";`
`   close;`

[Category:Script Command](/Category:Script_Command "wikilink")