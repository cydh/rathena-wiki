---
title: Getelementofarray
permalink: /Getelementofarray/
---

Syntax
------

-   **getelementofarray**(<array variable>, <index>);

Description
-----------

This command retrieves the value of the element of given array at given index. This is equivalent to using:

`array[index]`

The reason for this is, that this short form is internally converted into a call to getelementofarray, when the script is loaded.

Examples
--------

[`setarray`](/setarray "wikilink")` @array[0], 1, 2, 3;`
[`set`](/set "wikilink")` @varl, getelementofarray(@array, 2);  // retrieves 3`
`set @vars, @array[2];  // retrieves 3 as well`
[`if`](/if "wikilink")`(@varl!=@vars)`
`{`
`    `[`mes`](/mes "wikilink")` "This will never be shown";`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")