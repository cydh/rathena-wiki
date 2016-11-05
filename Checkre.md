---
title: Checkre
permalink: /Checkre/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   **checkre**(<type>)

Description
-----------

This allows you to check if a renewal feature is enabled or not in renewal.h, and returns 1 if enabled and 0 for disabled.

The renewal feature to check is determined by type.

`0 - RENEWAL (game renewal server mode)`
`1 - RENEWAL_CAST (renewal cast time)`
`2 - RENEWAL_DROP (renewal drop rate algorithms)`
`3 - RENEWAL_EXP (renewal exp rate algorithms)`
`4 - RENEWAL_LVDMG (renewal level modifier on damage)`
`5 - RENEWAL_ASPD (renewal ASPD)`

Example
-------

`        if( checkre(0) )`
`             dispbottom "You are using Renewal Game Settings";`
`        else`
`             dispbottom "You are using Pre-Renewal Game Setting";`

You can use as well the following links as references:

-   [trunk/npc/airports/airships.txt](http://trac.rathena.org/browser/rathena/trunk/npc/airports/airships.txt#L656)
-   Changeset [16545](http://trac.rathena.org/changeset/16545/rathena)
