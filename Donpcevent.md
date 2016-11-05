---
title: Donpcevent
permalink: /Donpcevent/
---

Syntax
------

-   **donpcevent** &lt;"event label"&gt;;
-   **cmdothernpc** &lt;"npc name"&gt;, &lt;"command"&gt;;

Description
-----------

This command invokes the event label code within an another [NPC](/NPC "wikilink") or NPCs. If *event label* has the form "NpcName::OnLabel", then only given NPC's event label will be invoked (much like [goto](/goto "wikilink") into another NPC). If the form is "::OnLabel" (*NpcName* ommited), the event code of all NPCs with given label will be invoked, one after another. In both cases the invoked script will run without an attached [RID](/RID "wikilink"), whether or not the invoking script was attached to a player. The event label name is required to start with *On*.

This command can be used to make other NPCs act, as if they were responding to the invoking NPC's actions, such as using an [emotion](/emotion "wikilink") or [talking](/npctalk "wikilink").

The command **cmdothernpc** is equivalent to **donpcevent** "<npc name>::OnCommand<command>" and an approximation to the [AEGIS](/AEGIS "wikilink") script command with same name.

Examples
--------

`prontera,150,150,3 script  NPC 53,{`
`    `[`mes`](/mes "wikilink")` "Hey NPC2 copies what I do.";`
`    `[`close2`](/close2 "wikilink")`;`
`    `[`set`](/set "wikilink")` .@emote, `[`rand`](/rand "wikilink")`(1,30);`
`    donpcevent "NPC2::OnEmote";`
`OnEmote:`
`    `[`emotion`](/emotion "wikilink")` .@emote;`
`    `[`end`](/end "wikilink")`;`
`}`
`prontera,152,150,5 script  NPC2    53,{`
`    mes "Hey NPC copies what I do.";`
`    close2;`
`    set .@emote, rand(1,30);`
`    donpcevent "NPC::OnEmote";`
`OnEmote:`
`    emotion .@emote;`
`    end;`
`}`

Whichever of the both NPCs is talked to, both will show a random emotion at the same time.

See Also
--------

-   [doevent](/doevent "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")