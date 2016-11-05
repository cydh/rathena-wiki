---
title: Getiteminfo
permalink: /Getiteminfo/
---

Syntax
------

-   [getiteminfo](/getiteminfo "wikilink")(<item ID>,<type>)

Description
-----------

This function will look up the item with the specified ID number in the database and return the info set by TYPE argument. It will return -1 if there is no such item.

### Valid Types

| Value | Type                                                             |
|-------|------------------------------------------------------------------|
| 0     | Buy Price                                                        |
| 1     | Sell Price                                                       |
| 2     | Item Type                                                        |
| 3     | MaxChance (Max drop chance of this item e.g. 1 = 0.01% , etc..

         -   0 means monsters don't drop it at all (rare or a quest item)
         -   10000 means this item is sold in NPC shops only               |
| 4     | Sex                                                              |
| 5     | Equip                                                            |
| 6     | Weight                                                           |
| 7     | Atk                                                              |
| 8     | Def                                                              |
| 9     | Range                                                            |
| 10    | Slots                                                            |
| 11    | Look                                                             |
| 12    | Equip Level                                                      |
| 13    | Weapon Level                                                     |
| 14    | View ID                                                          |

Example
-------

[Category:Script Command](/Category:Script_Command "wikilink")