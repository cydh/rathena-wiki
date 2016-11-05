---
title: OnPCDieEvent
permalink: /OnPCDieEvent/
---

Syntax
------

[OnPCDieEvent](/OnPCDieEvent "wikilink"):

Explanation
-----------

This special label triggers when a player dies. The variable '[killerrid](/killerrid "wikilink")' is set to the ID of the killer.

It is often used in PVP scripts that record kills/deaths or display messages when you kill someone or are killed.

Examples
--------

This will display a message to players who die on guild_vs1, and also announce a message to that map.

`-  script  pvp_die_message -1,{`
[`OnPCDieEvent`](/OnPCDieEvent "wikilink")`:`
`   `[`if`](/if "wikilink")` (`[`strcharinfo`](/strcharinfo "wikilink")`(3) == "guild_vs1") {`
`       `[`dispbottom`](/dispbottom "wikilink")` "You just died.";`
`       `[`mapannounce`](/mapannounce "wikilink")` `[`strcharinfo`](/strcharinfo "wikilink")`(3), strcharinfo(0) + " has died.  What a pity!",bc_map;`
`   }`
`   `[`end`](/end "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")