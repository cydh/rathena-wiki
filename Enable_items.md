---
title: Enable items
permalink: /Enable_items/
---

Syntax
------

-   **enable_items**;
-   **disable_items**;

Description
-----------

These commands enable and disable item usage and equipping while scripts are running in a particular [NPC](/NPC "wikilink") for the [currently attached](/RID#Usage "wikilink") character. Item usage and equipping is disabled in all NPCs by default, to prevent possible exploits.

Items can be enabled for only single NPC at same time, each new call to enable_items or disable_items will affect any following scripts. When item usage is enabled for a particular NPC, it will last until either disable_items is called or the character logs out, which usually is not desired, thus disable_items should be called as soon as possible, when item usage in scripts is no longer needed.

Examples
--------

[`set`](/set "wikilink")` .@potcount, `[`countitem`](/countitem "wikilink")`(569);`
[`getitem`](/getitem "wikilink")` 569, 1;  // Novice_Potion`
`enable_items;`
[`mes`](/mes "wikilink")` "[Tutor]";`
`mes "I gave you a "+`[`getitemname`](/getitemname "wikilink")`(569)+", try to drink it.";`
`mes "";`
`mes "Note, if you try to fool me and do not use, I'll take it again from you.";`
[`next`](/next "wikilink")`;`
`disable_items;`
`mes "[Tutor]";`
[`if`](/if "wikilink")`(countitem(569)>.@potcount)`
`{`
`    `[`delitem`](/delitem "wikilink")` 569, 1;`
`    mes "I said, I will take it back, when you do not drink it.";`
`}`
`else`
`{`
`    mes "Well done.";`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")