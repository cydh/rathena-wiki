---
title: Savepoint
permalink: /Savepoint/
---

Syntax
------

-   **save** &lt;"map name"&gt;, <x>, <y>;
-   **savepoint** &lt;"map name"&gt;, <x>, <y>;

Description
-----------

This command stores the location, where the [invoking character](/RID#Usage "wikilink") will be warped to, when re-spawning after death, getting warped out of a [WoE](/WoE "wikilink") castle or using skill Teleport Lv2. Map flags, which would otherwise prohibit setting a save point or warping to a map, are ignored by this script command. Both versions of the command are equivalent.

Examples
--------

[`mes`](/mes "wikilink")` "[Kafra Employee]";`
`mes "Your Respawn Point";`
`mes "has been saved here";`
`mes "in the city of Payon.";`
`mes "Thank you for using";`
`mes "the Kafra Services.";`
`savepoint "payon", 257, 242;`
[`close2`](/close2 "wikilink")`;`
[`cutin`](/cutin "wikilink")` "", 255;`
[`end`](/end "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink")