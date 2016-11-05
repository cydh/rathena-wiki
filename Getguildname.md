---
title: GetGuildName
permalink: /GetGuildName/
---

Syntax
------

-   **getguildname**(<guild id>)

Description
-----------

This function returns a guild's name given an ID number. If there is no such guild, "null" will be returned;
This is used all over the WoE controlling scripts. You could also use it for a guild-based event.

Examples
--------

`// Would print what ever guild 10007 is, in my case this would return "AlcoROhics"`
[`mes`](/mes "wikilink")` "The guild "+`**`GetGuildName`**`(10007)+" are all nice people.";`

`// This will do the same as above:`
[`set`](/set "wikilink")` @var,10007;`
[`mes`](/mes "wikilink")` "We have some friends in "+`**`GetGuildName`**`(@var)+", you know.";`

[announce](/announce "wikilink") "The \[" + [getcastlename](/getcastlename "wikilink")([strnpcinfo](/strnpcinfo "wikilink")(2)) + "\] castle has been conquered by the \[" + **getguildName**(.@GID) + "\] guild.",bc_all|bc_woe;

[Category:Script_Command](/Category:Script_Command "wikilink")