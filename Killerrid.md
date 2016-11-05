---
title: Killerrid
permalink: /Killerrid/
---

Syntax
------

[killerrid](/killerrid "wikilink")

Explanation
-----------

This special variable is set when a player dies and [OnPCDieEvent](/OnPCDieEvent "wikilink") is triggered. [killerrid](/killerrid "wikilink") is set to the [RID](/RID "wikilink") of the killer.

You can use [rid2name](/rid2name "wikilink")([killerrid](/killerrid "wikilink")) to get the player name.

Examples
--------

This will announce the KillerName and the name of player that has been killed.

`-  script  pvp_die_message -1,{`
[`OnPCDieEvent`](/OnPCDieEvent "wikilink")`:`
`   `[`announce`](/announce "wikilink")` `[`rid2name`](/rid2name "wikilink")`(`[`killerrid`](/killerrid "wikilink")`) + " just killed " + `[`strcharinfo`](/strcharinfo "wikilink")`(0),bc_all;`
`   `[`end`](/end "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")