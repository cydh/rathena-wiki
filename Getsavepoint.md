---
title: Getsavepoint
permalink: /Getsavepoint/
---

Syntax
------

-   [getsavepoint](/getsavepoint "wikilink")(<information type>)

Description
-----------

This function will return information about the invoking character's save point. You can use it to let a character swap between several recorded save points. Available information types are:

-   0 - Map name (a string)
-   1 - X coordinate
-   2 - Y coordinate

Examples
--------

[`mes`](/mes "wikilink")` "I see you save on the map, " + `[`getsavepoint`](/getsavepoint "wikilink")`(0);`
`mes "at the coordinates ("+getsavepoint(1)+","+getsavepoint(2)+")";`

[Category:Script Command](/Category:Script_Command "wikilink")