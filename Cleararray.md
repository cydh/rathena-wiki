---
title: Cleararray
permalink: /Cleararray/
---

Syntax
------

-   **cleararray** <array variable>, <value>, <amount of values to set>;

Description
-----------

This command sets a range of elements in an array to given value. If you specify an array variable without index, then index 0 is assumed, otherwise the value setting will start from given index.

Examples
--------

[`setarray`](/setarray "wikilink")` @array[0], 100, 100, 100, 100, 100, 100, 100, 100, 100, 100, 100;`
`cleararray @array[0], 100, 11;`

Both lines result in the same array, but using cleararray saves typing.

`cleararray @array[0], 0, 127;  // number array`
`cleararray @strarray$[0], "", 127; // string array`

Deletes entire array.

`setarray @array[0], 1, 2, 3, 4, 5, 6;`
`cleararray @array[2], 0, 2;`

Results in array { 1, 2, 0, 0, 5, 6 }.

[Category:Script Command](/Category:Script_Command "wikilink")