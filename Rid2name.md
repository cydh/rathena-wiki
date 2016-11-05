---
title: Rid2name
permalink: /Rid2name/
---

Syntax
------

-   **rid2name**(<rid>);

Description
-----------

This command returns a display name for given [RID](/RID "wikilink"). This is not only limited to players, but also displays name of [monsters](/mob "wikilink"), [NPCs](/NPC "wikilink"), pets, homunculus and mercenaries. If the RID is of unknown type, "" is returned together with an error. If there is no such RID, "(null)" is returned with an error. In both cases the script execution will continue.

Note, that [killedrid](/killedrid "wikilink") of a monster cannot be used in this command, because it is a mob class id.

Examples
--------

`-  script  DeathAnnouncer  -1,{`
[`OnPCDieEvent`](/OnPCDieEvent "wikilink")`:`
`    `[`dispbottom`](/dispbottom "wikilink")` "You have been killed by "+rid2name(`[`killerrid`](/killerrid "wikilink")`)+".";`
`    `[`end`](/end "wikilink")`;`
`}`

This will announce to each player, whenever they get killed, who did the finishing blow.

[Category:Script Command](/Category:Script_Command "wikilink")