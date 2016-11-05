---
title: Doevent
permalink: /Doevent/
---

Syntax
------

-   **doevent** &lt;"event label"&gt;;

Description
-----------

This command invokes a script at given event label in an another [NPC](/NPC "wikilink"). The parameter *event label* has the form "NpcName::OnLabel" and unlike in [donpcevent](/donpcevent "wikilink"), it cannot target multiple NPCs by omitting the NPC name. It works much like a [goto](/goto "wikilink") command into an another NPC. If there was an [RID](/RID "wikilink") attached to the invoking script, it will be attached to the invoked script as well.

This command is not used very much, because it is more limited than donpcevent and passing RID to another script is usually not required.

Examples
--------

`prontera,150,150,3 script  NPC1    53,{`
`    `[`mes`](/mes "wikilink")` "Let's see, no one look, so let as deal.";`
`    `[`next`](/next "wikilink")`;`
`    doevent "NPC2::OnTalk";`
`    mes "Damn, we were spotted, so no trade for you.";`
`    `[`close`](/close "wikilink")`;`
`}`
`prontera,152,150,5 script  NPC2    53,{`
`    // ...`
`OnTalk:`
`    `[`npctalk`](/npctalk "wikilink")` "Everyone look, "+`[`strcharinfo`](/strcharinfo "wikilink")`(0)+" tries to buy forbidden goods!";`
`    `[`end`](/end "wikilink")`;`
`}`

Every time a player talks to NPC1, NPC2 will scream into it's area, what the player is about to do. Since doevent passes the RID to NPC2, it can use strcharinfo to retrieve the player's name.

[Category:Script Command](/Category:Script_Command "wikilink")