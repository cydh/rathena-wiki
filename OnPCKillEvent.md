---
title: OnPCKillEvent
permalink: /OnPCKillEvent/
---

Syntax
------

[OnPCKillEvent](/OnPCKillEvent "wikilink"):

Explanation
-----------

This special label triggers when a player kills another player. The variable 'killedrid' is set to the ID of the player killed.

It is often used in PVP scripts that record kills/deaths or display messages when you kill someone or are killed.

Examples
--------

This will display a message to players who kill other players on guild_vs1, and also announce a message to that map.

`-  script  pvp_kill_message    -1,{`
[`OnPCKillEvent`](/OnPCKillEvent "wikilink")`:`
`   `[`if`](/if "wikilink")` (`[`strcharinfo`](/strcharinfo "wikilink")`(3) == "guild_vs1") {`
`       `[`dispbottom`](/dispbottom "wikilink")` "You just killed someone.";`
`       `[`mapannounce`](/mapannounce "wikilink")` `[`strcharinfo`](/strcharinfo "wikilink")`(3), strcharinfo(0) + " is a killer!",bc_map;`
`   }`
`   `[`end`](/end "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")