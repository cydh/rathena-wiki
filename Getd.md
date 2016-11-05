---
title: Getd
permalink: /Getd/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [getd](/getd "wikilink")("<variable name>");

Description
-----------

Returns a reference to a variable, the name can be constructed dynamically. Refer to [setd](/setd "wikilink") for usage.

This can also be used to set an array dynamically:

` setarray getd(".array[0]"), 1, 2, 3, 4, 5;`

Examples
--------

[`set`](/set "wikilink")` .@mob_id, 1002;`
[`dispbottom`](/dispbottom "wikilink")` getd(".prize_" + .@mob_id); // displays the value of .prize_1002`