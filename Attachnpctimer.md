---
title: Attachnpctimer
permalink: /Attachnpctimer/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [attachnpctimer](/attachnpctimer "wikilink") {"Character Name"};

Description
-----------

**AttachNPCTimer** allows you to attach a player to a NPC later on. This can only be done to the NPC Timer that is in the same NPC as where this command is used. To attach a player, you will simply have to give his account id or RID (or UID/GID in some devs words) as a parameter.The '[setnpctimer](/setnpctimer "wikilink")' command will explicitly set the timer to a given tick. '[getnpctimer](/getnpctimer "wikilink")' provides timer information. Its parameter defines what type:
== Examples ==

`attachnpctimer getcharid(3); // Attaches current player to the NPC Timer.`
`attachnpctimer 2000000; // Attaches the player with account id 2000000 to the NPC Timer, if he is online.`