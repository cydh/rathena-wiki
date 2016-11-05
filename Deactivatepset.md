---
title: Deactivatepset
permalink: /Deactivatepset/
---

Syntax
------

-   **deactivatepset** <set number>;

Description
-----------

This command disables previously enabled set of [PCRE](/PCRE "wikilink") patterns from firing. The expressions themselves remain defined, and can be re-enabled with [activatepset](/activatepset "wikilink"). To remove a pattern set completely, [deletepset](/deletepset "wikilink") must be used.

If -1 is passed as set number, all currently defined sets are disabled.

Examples
--------

`deactivatepset -1;`
[`activatepset`](/activatepset "wikilink")` 2;`

Disables all currently enabled pattern sets and enables only pattern set 2 (assumed to be previously defined).

[Category:Script Command](/Category:Script_Command "wikilink")