---
title: Getitemname
permalink: /Getitemname/
---

Syntax
------

-   **getitemname**(<item id>);

Description
-----------

Retrieves the display name for an item given by ID from the 3rd column in the item database. If there is no such item, "null" is returned as name.

Examples
--------

[`mes`](/mes "wikilink")` "See? Whenever you find some "+getitemname(512)+", bring it to me.";`

Will turn into: "See? Whenever you find some Apple, bring it to me."

`mes "See? Whenever you find some "+getitemname(12)+", bring it to me.";`

Since there is usually no item with ID 12, this will turn into: "See? Whenever you find some null, bring it to me."

[Category:Script Command](/Category:Script_Command "wikilink")