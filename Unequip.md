---
title: Unequip
permalink: /Unequip/
---

Syntax
------

-   **unequip** <equipment slot>;

Description
-----------

This command will unequip whatever is currently equipped in the [invoking](/RID "wikilink") character's specified equipment slot, which can be:

|                         |                           |
|-------------------------|---------------------------|
| **EQI_HEAD_TOP (1)**  | Upper headgear            |
| **EQI_ARMOR (2)**      | Armor                     |
| **EQI_HAND_L (3)**    | Left hand (weapon/shield) |
| **EQI_HAND_R (4)**    | Right hand (weapon)       |
| **EQI_GARMENT (5)**    | Garment                   |
| **EQI_SHOES (6)**      | Shoes                     |
| **EQI_ACC_L (7)**     | Left accessory            |
| **EQI_ACC_R (8)**     | Right accessory           |
| **EQI_HEAD_MID (9)**  | Middle headgear           |
| **EQI_HEAD_LOW (10)** | Lower headgear            |

If an item occupies several equipment slots, it will get unequipped from all of them.

Examples
--------

[`OnTouch`](/OnTouch "wikilink")`:`
`    `[`if`](/if "wikilink")`(`[`getequipid`](/getequipid "wikilink")`(EQI_SHOES)!=-1)`
`    {`
`        unequip EQI_SHOES;`
`        `[`mes`](/mes "wikilink")` "";`
`        mes "^808080Shoes are banned from this sacred place.^000000";`
`        `[`close`](/close "wikilink")`;`
`    }`
`    `[`end`](/end "wikilink")`;`

When a player steps into the protected area with shoes equipped, they are taken off.

See Also
--------

-   [nude](/nude "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")