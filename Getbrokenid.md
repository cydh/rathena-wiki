---
title: Getbrokenid
permalink: /Getbrokenid/
---

Syntax
------

-   [getbrokenid](/getbrokenid "wikilink")(<number>)

Description
-----------

This function will search the invoking character's inventory for any broken items, and will return their item ID numbers. Since the character may have several broken items, 1 given as an argument will return the first one found, 2 will return the second one, etc. Will return 0 if no such item is found.

Examples
--------

`// Let's see if they have anything broken:`
`   if (getbrokenid(1)==0) goto Skip;`
`// They do, so let's print the name of the first broken item:`
`   mes "Oh, I see you have a broken "+getitemname(getbrokenid(1))+" here!";`
`Skip:`
`   mes "You don't have anything broken, quit bothering me.";`

[Category:Script Command](/Category:Script_Command "wikilink")