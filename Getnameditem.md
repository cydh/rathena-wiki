---
title: Getnameditem
permalink: /Getnameditem/
---

Syntax
------

-   [getnameditem](/getnameditem "wikilink")(<item id>, <char id>)
-   [getnameditem](/getnameditem "wikilink")("<item name>", <char id>)
-   [getnameditem](/getnameditem "wikilink")(<item id>, "<char name>")
-   [getnameditem](/getnameditem "wikilink")("<item name>", "<char name>")

Description
-----------

This function is equivalent to using 'getitem', however, it will not just give the character an item object, but will also inscribe it with a specified character's name. The player whose name will be inscribed on the item must be online. You may not inscribe items with arbitrary strings, only with names of characters that actually exist. While this isn't said anywhere specifically, apparently, named items may not have cards in them, slots or no - these data slots are taken by the character ID who's name is inscribed. Only one remains free and it's not quite clear if a card may be there.

This function will return 1 if an item was successfully created and 0 if it wasn't for whatever reason. Like 'getitem', this function will also accept an 'english name' from the item database as an item name and will return 0 if no such item exists.

Examples
--------

The command is equivalent to:

[`getitem2`](/getitem2 "wikilink")` `<item id>`, 1, 1, 0, 0, 254, 0, `<char id>` & 65535, `<char id>` >> 16;`

[`mes`](/mes "wikilink")` "Here you have your own arrow.";`
[`getnameditem`](/getnameditem "wikilink")` 1750, `[`getcharid`](/getcharid "wikilink")`(0);  // Arrow`

Gives the character 1 arrow with it's own name.

[Category:Script Command](/Category:Script_Command "wikilink")