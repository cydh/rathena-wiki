---
title: Getpartyname
permalink: /Getpartyname/
---

Syntax
------

-   [getpartyname](/getpartyname "wikilink")(<party id>)

Description
-----------

This function will return the name of a party that has the specified ID number. If there is no such party ID, "null" will be returned.

Lets say the ID of a party was saved as a global variable:

Examples
--------

`// This would return the name of the party from the ID stored in a variable`
[`mes`](/mes "wikilink")` "You're in the "+ `[`getpartyname`](/getpartyname "wikilink")`($@var) +" party, I know!";`

[Category:Script Command](/Category:Script_Command "wikilink")