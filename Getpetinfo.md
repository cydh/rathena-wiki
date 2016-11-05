---
title: Getpetinfo
permalink: /Getpetinfo/
---

Syntax
------

-   **getpetinfo**(<type>);

Description
-----------

This function will return pet information for the pet the [invoking character](/RID "wikilink") currently has active. Valid types are:

-   0 - Database ID
-   1 - Class
-   2 - Name
-   3 - Friendly level (intimacy score), 1000 is full loyalty
-   4 - Hungry level, 100 is completely full.
-   5 - Pet rename flag. 0 means this pet has not been named yet
-   6 - Pet level

If the character does not have a pet, the command returns "null" for name and 0 for all other types.

Examples
--------

[`switch`](/switch "wikilink")`(getpetinfo(1))`
`{`
`    case 1002:  // Poring`
`    case 1113:  // Drops`
`    case 1031:  // Poporing`
`    case 1057:  // Yoyo`
`        `[`mes`](/mes "wikilink")` "Sorry, but looter pets are not allowed here.";`
`        mes "Please put your "+getpetinfo(2)+" into it's egg.";`
`        `[`close`](/close "wikilink")`;`
`}`

See Also
--------

-   [gethominfo](/gethominfo "wikilink")
-   [getmercinfo](/getmercinfo "wikilink")
-   [getmonsterinfo](/getmonsterinfo "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")