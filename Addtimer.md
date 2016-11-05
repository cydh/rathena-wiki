---
title: Addtimer
permalink: /Addtimer/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [addtimer](/addtimer "wikilink") <ticks>,"NPC::OnEvent";
-   [addtimercount](/addtimercount "wikilink") <ticks>,"NPC::OnEvent";
-   [deltimer](/deltimer "wikilink") "NPC::OnEvent";

Description
-----------

These commands will create, destroy, and delay a countdown timer - 'addtimer' to create, 'deltimer' to destroy and 'addtimercount' to delay it by the specified number of ticks. For all three cases, the event label given is the identifier of that timer. The timer runs on the character object that is attached to the script (and I'm not sure what happens when nothing is attached), and can have multiple instances. When the label is ran, it is ran as if the player that the timer runs on has clicked the NPC.

When this timer runs out, a new execution thread will start in the specified NPC object at the specified label. If no such label is found in the NPC object, it will run as if clicked.

The ticks are given in 1/1000ths of a second.