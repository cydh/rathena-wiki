---
title: Setd
permalink: /Setd/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [setd](/setd "wikilink") "<variable name>",<value>;

Description
-----------

Works almost identical as [set](/set "wikilink"), just that the variable name is identified as a string, thus can be constructed dynamically.

This command is equivalent to:

`set `[`getd`](/getd "wikilink")`("variable name"),`<value>`;`

Examples
--------

`set .@mob_id, 1002;`
`setd ".prize_" + .@mob_id, 911; // sets the value of .prize_1002 to 911`