---
title: Itemheal
permalink: /Itemheal/
---

Syntax
------

-   **itemheal** <hp>, <sp>;

Description
-----------

This command heals given absolute amounts of HP and/or SP on the invoking character. Unlike [heal](/heal "wikilink"), this command is intended for use in item scripts. It applies potion-related bonuses, such as alchemist ranking, cards and status changes. When used inside an NPC script, certain bonuses are omitted.

Examples
--------

`itemheal `[`rand`](/rand "wikilink")`(100,150),0;`

This heals between 100 and 150 HP and no SP.

See Also
--------

-   [heal](/heal "wikilink")
-   [percentheal](/percentheal "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")