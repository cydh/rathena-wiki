---
title: Deletearray
permalink: /Deletearray/
---

Syntax
------

-   **deletearray** <array>, <amount of elements to delete>;

Description
-----------

This command deletes a range of values within given array and shifts remaining values to fill the deletion gap.

**Important:** Currently (r14395) the command uses [getarraysize](/getarraysize "wikilink") internally, which leads to unpredictable results with arrays, that contain empty elements. It is recommended to use a combination of [copyarray](/copyarray "wikilink") and [cleararray](/cleararray "wikilink") instead.

Examples
--------

**`deletearray`**` @array, 10;`

Deletes the first 10 elements of the array and shifts all other values by one to the left.

[`copyarray`](/copyarray "wikilink")` @array[0], @array[10], 90;`
[`cleararray`](/cleararray "wikilink")` @array[90], 0, 10;`

Assuming *@array* has 100 elements, this achieves the same effect as the example above, but works properly even if *@array* has empty element(s).

[Category:Script Command](/Category:Script_Command "wikilink")