---
title: Getequiprefinerycnt
permalink: /Getequiprefinerycnt/
---

Syntax
------

-   **getequiprefinerycnt**(<equipment slot>)

Description
-----------

This returns the current refine level for a particular item in the specified equipment slot.

### Slot Values

| Value | Type            |
|-------|-----------------|
| 1     | Upper Headgear  |
| 2     | Armor           |
| 3     | Left Hand       |
| 4     | Right Hand      |
| 5     | Garment         |
| 6     | Foot Gear       |
| 7     | Accessory 1     |
| 8     | Accessory 2     |
| 9     | Middle Headgear |
| 10    | Lower Headgear  |

Example
-------

This can be used to check if you have reached a maximum refine value, default for this is +10:

`       `[`if`](/if "wikilink")`(`**`getequiprefinerycnt`**`(EQI_HEAD_TOP) < 10) goto L_Refine_HeadGear;`
`       `[`mes`](/mes "wikilink")` "Sorry, it's not possible to refine hats better than +10";`
`       `[`close`](/close "wikilink")`;`
`   L_Refine_HeadGear:`
`       mes "I will now upgrade your "+getequipname(EQI_HEAD_TOP);`