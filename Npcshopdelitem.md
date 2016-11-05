---
title: Npcshopdelitem
permalink: /Npcshopdelitem/
---

Syntax
------

-   **npcshopdelitem** "<name>",<item id>{,<item id>{,<item id>{,...}}}

Description
-----------

This command will remove items from the specified NPC shop or cashshop. If the item to remove exists more than once on the shop, all instances will be removed.

Note that the function returns 1 even if no items were removed. The return value is only to confirm that the shop was indeed found.

Examples
--------

If you have an item in a shop that is for promotional events only, then you can remove the item using a script, if that script also ends the event.

`   -   script  endsummerevent  -1,{`
[`OnClock`](/OnClock "wikilink")`0000:`
`   `[`if`](/if "wikilink")`(`[`gettime`](/gettime "wikilink")`(6)==9 && gettime(5)==1){`
`       `<other even ending code here>
`       `[`disablenpc`](/disablenpc "wikilink")` "Summer Event";`
`       `**`npcshopdelitem`**` "V4P Shop",501;`
`       `[`announce`](/announce "wikilink")` "Event NPCs disabled and promo items removed from V4P shop!",0;`
`   }`
[`close`](/close "wikilink")`;`
`}`

The above example will remove the item Red Potion from the 'V4P Shop' shop NPC then make an announcement on the 1st of September at 0000hrs. It is an **example only** and is not guaranteed to work.

Related Commands: [npcshopitem](/npcshopitem "wikilink"), [npcshopadditem](/npcshopadditem "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")