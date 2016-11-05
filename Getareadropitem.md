---
title: Getareadropitem
permalink: /Getareadropitem/
---

Syntax
------

-   [getareadropitem](/getareadropitem "wikilink")("<map name>",<x1>,<y1>,<x2>,<y2>,<item id>)
-   [getareadropitem](/getareadropitem "wikilink")("<map name>",<x1>,<y1>,<x2>,<y2>,"<item name>")

Description
-----------

This function will count all the items with the specified ID number lying on the ground on the specified map within the x1/y1-x2/y2 square on it and return that number.

This is the only function around where a parameter may be either a string or a number! If it's a number, it means that only the items with that item ID number will be counted. If it is a string, it is assumed to mean the 'english name' field from the item database. If you give it an empty string, or something that isn't found from the item database, it will count item number '512' (Apples).

Examples
--------

[Category:Script Command](/Category:Script_Command "wikilink")