---
title: Isequipped
permalink: /Isequipped/
---

Syntax
------

-   **isequipped**(<id>{,<id>{,<id>{,<id>}}})

Description
-----------

This function will return 1 if the invoking character has all of the item IDs given equipped (if card IDs are passed, then it checks if the cards are inserted into slots in the equipment they are currently wearing). Theoretically there is no limit to the number of items that may be tested for at the same time. If even one of the items given is not equipped, 0 will be returned.
The function was meant for item scripts to support the cards released by Gravity in February 2005, but it will work just fine in normal NPC scripts.

Examples
--------

`// (Poring,Santa Poring,Poporing,Marin)`
[`if`](/if "wikilink")` (isequipped(4001,4005,4033,4196)) `[`mes`](/mes "wikilink")` "Wow! You're wearing a full complement of possible poring cards!";`
`// (Poring)`
[`if`](/if "wikilink")` (isequipped(4001)) `[`mes`](/mes "wikilink")` "A poring card is useful, don't you think?";`
`   `

You can also have the checks in an item script:
**{** [if](/if "wikilink")(isequipped(1602,4004,4004,4004,4004)) {

`   `[`dispbottom`](/dispbottom "wikilink")` "Awarded +3 Int for having 4 Drops Cards in a Rod[4]."; `[`bonus`](/bonus "wikilink")` bInt,10;`
`} `[`else`](/else "wikilink")` { `
`   `[`dispbottom`](/dispbottom "wikilink")` "4 Drops Cards in a Rod[4] for an extra bonus!";`
`} `**`}`**`,`**`{}`**`,`**`{}`**

[Category:Script_Command](/Category:Script_Command "wikilink")