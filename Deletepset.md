---
title: Deletepset
permalink: /Deletepset/
---

Syntax
------

-   **deletepset** <set number>;

Description
-----------

This command deletes previously defined [PCRE](/PCRE "wikilink") pattern set, so a new one can be [defpattern](/defpattern "wikilink")'ed. To only disable one or all pattern sets, [deactivatepset](/deactivatepset "wikilink") must be used. Unlike deactivatepset, this command does not support -1 as *set number*, to delete all pattern sets.

Examples
--------

`deletepset 1;`
[`defpattern`](/defpattern "wikilink")` 1, "([^:]+):.*\\ssorry.*", "Lquote3";`

Deletes previously defined pattern set 1, to set up a new one.

[Category:Script Command](/Category:Script_Command "wikilink")