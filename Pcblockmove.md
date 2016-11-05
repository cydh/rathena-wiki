---
title: Pcblockmove
permalink: /Pcblockmove/
---

Syntax
------

-   [pcblockmove](/pcblockmove "wikilink") <id>,<option>;

Description
-----------

Prevents the given ID from moving when the option != 0, and 0 enables the ID to move again. The ID can either be the [GID](/GID "wikilink") of a monster/NPC or account ID of a character, and will run for the attached player if zero is supplied.

Examples
--------

`// Prevents the current char from moving away.`
[`pcblockmove`](/pcblockmove "wikilink")` `[`getcharid`](/getcharid "wikilink")`(3),1;`

`// Enables the current char to move again.`
[`pcblockmove`](/pcblockmove "wikilink")` `[`getcharid`](/getcharid "wikilink")`(3),0;`

[Category:Script Command](/Category:Script_Command "wikilink")