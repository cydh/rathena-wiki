---
title: Percentheal
permalink: /Percentheal/
---

Syntax
------

-   **percentheal** <hp>, <sp>;

Description
-----------

This command modifies the HP and/or SP of the [currently attached](/RID#Usage "wikilink") character. The passed values are in percent of the maximum HP and SP respectively. Positive values will heal, negative ones will cause damage.

The character will not die from the damage unless -100 is passed for HP. Passing -99 and -1 consecutively will leave the character alive with 1 HP. Only HP and/or SP is modified, no further effects are shown. If absolute values should be healed or drained, [heal](/heal "wikilink") is to be used instead.

Examples
--------

`percentheal 100, 0;  // Heals 100% HP`
`percentheal 0, 100;  // Heals 100% SP`
`percentheal 50, 50;  // Heals 50% HP and 50% SP`
`percentheal 0, -50;  // Drains 50% SP`
`percentheal -100, 0;  // Drains all HP and kills the player`

[Category:Script Command](/Category:Script_Command "wikilink")