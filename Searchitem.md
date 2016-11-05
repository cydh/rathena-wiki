---
title: Searchitem
permalink: /Searchitem/
---

Syntax
------

-   [searchitem](/searchitem "wikilink") <array name>,"<item name>";

Description
-----------

This command will fill the given array with the ID of items whose name matches the given one. It returns the number of items found. For performance reasons, the results array is limited to 10 items.

Examples
--------

`   `[`mes`](/mes "wikilink")` "What item are you looking for?";`
`   `[`input`](/input "wikilink")` @name$;`
`   `[`set`](/set "wikilink")` @qty, `[`searchitem`](/searchitem "wikilink")`(@matches[0],@name$);`
`   `[`mes`](/mes "wikilink")` "I found "+@qty+" items:";`
`   `[`for`](/for "wikilink")` (`[`set`](/set "wikilink")` @i, 0; @i < @qty; `[`set`](/set "wikilink")` @i, @i+1)`
`       //Display name (eg: "Apple[0]")`
`       `[`mes`](/mes "wikilink")` `[`getitemname`](/getitemname "wikilink")`(@matches[@i])+"["+`[`getitemslots`](/getitemslots "wikilink")`(@matches[@i])+"]";`

[Category:Script Command](/Category:Script_Command "wikilink")