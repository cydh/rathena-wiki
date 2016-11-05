---
title: Getarraysize
permalink: /Getarraysize/
---

Syntax
------

-   [getarraysize](/getarraysize "wikilink")(<array name>)

Description
-----------

This function returns the number of values that are contained inside the specified array. Notice that zeros and empty strings at the end of this array are not counted towards this number.

Examples
--------

[`setarray`](/setarray "wikilink")` @array[0], 100, 200, 300, 400, 500, 600;`
[`set`](/set "wikilink")` @arraysize, `[`getarraysize`](/getarraysize "wikilink")`(@array);`

This will make @arraysize == 6. But if you try this:

[`setarray`](/setarray "wikilink")` @array[0], 100, 200, 300, 400, 500, 600, 0;`
[`set`](/set "wikilink")` @arraysize, `[`getarraysize`](/getarraysize "wikilink")`(@array);`

@arraysize will still equal 6, even though you've set 7 values.

[Category:Script Command](/Category:Script_Command "wikilink")