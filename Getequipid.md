---
title: Getequipid
permalink: /Getequipid/
---

Syntax
------

-   **getequipid**(<equipment slot>);

Description
-----------

This function returns the id of the item, which occupies given *equipment slot* on [currently attached](/RID#Usage "wikilink") character. When the slot is empty, -1 will be returned. If an item occupies multiple slots, each of them returns the same item id. Equipment slot can be one of the following constants:

| Value                            | Description               |
|----------------------------------|---------------------------|
| **EQI_HEAD_TOP (1)**           | Upper headgear            |
| **EQI_ARMOR (2)**               | Armor                     |
| **EQI_HAND_L (3)**             | Left hand (weapon/shield) |
| **EQI_HAND_R (4)**             | Right hand (weapon)       |
| **EQI_GARMENT (5)**             | Garment                   |
| **EQI_SHOES (6)**               | Shoes                     |
| **EQI_ACC_L (7)**              | Left accessory            |
| **EQI_ACC_R (8)**              | Right accessory           |
| **EQI_HEAD_MID (9)**           | Middle headgear           |
| **EQI_HEAD_LOW (10)**          | Lower headgear            |
| **EQI_COSTUME_HEAD_LOW (11)** | Lower Costume Headgear    |
| **EQI_COSTUME_HEAD_MID (12)** | Middle Costume Headgear   |
| **EQI_COSTUME_HEAD_TOP (13)** | Upper Costume Headgear    |
| **EQI_COSTUME_GARMENT (14)**   | Costume Garment           |

Examples
--------

[`if`](/if "wikilink")`((`[`getequipid`](/getequipid "wikilink")`(EQI_ARMOR)==2341) || (`[`getequipid`](/getequipid "wikilink")`(EQI_ARMOR)==2342))`
`{// equipped; there are two kinds of legion plate armor, with (2342)`
` // and without (2341) a card slot.`
`    `[`mes`](/mes "wikilink")` "You are wearing some "+`[`getitemname`](/getitemname "wikilink")`(2341)+",";`
`    `[`mes`](/mes "wikilink")` "please drop that in your stash before continuing";`
`}`
[`else`](/else "wikilink")` if((`[`countitem`](/countitem "wikilink")`(2341)>0) || (countitem(2342)>0))`
`{// inventory`
`    `[`mes`](/mes "wikilink")` "You have some "+getitemname(2341)+" in your"`
`    mes "inventory, please drop that in your stash";`
`    mes "before continuing";`
`}`
[`else`](/else "wikilink")
`{`
`    `[`mes`](/mes "wikilink")` "I will let you pass.";`
`    `[`close2`](/close2 "wikilink")`;`
`    `[`warp`](/warp "wikilink")` "place",50,50;`
`    `[`end`](/end "wikilink")`;`
`}`
[`close`](/close "wikilink")`;`

This makes players being able to warp into given place only, if they have neither legion plate armor equipped, nor in their inventory, to prevent them from equipping it later.

[Category:Script Command](/Category:Script_Command "wikilink")