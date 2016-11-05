---
title: Waitingroom
permalink: /Waitingroom/
---

Syntax
------

-   [waitingroom](/waitingroom "wikilink") &lt;"room name"&gt;, <limit>
-   [waitingroom](/waitingroom "wikilink") &lt;"room name"&gt;, <limit>\[, &lt;"event label"&gt;\];
-   [waitingroom](/waitingroom "wikilink") &lt;"room name"&gt;, <limit>\[, &lt;"event label"&gt;, <trigger>\];
-   [waitingroom](/waitingroom "wikilink") &lt;"room name"&gt;, <limit>\[, <trigger>, &lt;"event label"&gt;\];

Description
-----------

This command creates a waiting room above an [NPC](/NPC "wikilink") displaying the given *room name*. The *limit* parameter is a number specifying how many players can join the waiting room and can be between 0 and 20 (the maximum number of players allowed in a chat). By default, when the *limit* is reached, no more players may join but nothing will happen.

An *event label* can also be specified. The label must be in the format "NpcName::LabelName" similar to the [doevent](/doevent "wikilink") command. When an *event label* is declared, the script will be invoked at this label whenever the waitingroom reaches the *limit*. You can change when the script gets invoked by specifying a *trigger* number that is less than or equal to the *limit*. The *trigger* and the *event label* and be entered in any order as long as it comes after the *limit*.

Using the [enablewaitingroomevent](/enablewaitingroomevent "wikilink") and [disablewaitingroomevent](/disablewaitingroomevent "wikilink") commands will allow you to turn on and off the capacity trigger on the waiting room. You can later use the [delwaitingroom](/delwaitingroom "wikilink") command to close the waiting room.

Examples
--------

`prontera,150,150,3 script  WaitingNPC  53,{`
`   `[`if`](/if "wikilink")` ($@npcWaitingRoom) {`
`       `[`mes`](/mes "wikilink")` "The cool people wait here.";`
`   } `[`else`](/else "wikilink")` {`
`       mes "Let's wait for some cool people.";`
`       `[`set`](/set "wikilink")` $@npcWaitingRoom, 1;`
`       `[`waitingroom`](/waitingroom "wikilink")` "The Cool People",15,"WaitingNPC::OnFull",15;`
`       `[`enablewaitingroomevent`](/enablewaitingroomevent "wikilink")` "WaitingNPC";`
`   }`
`   `[`close`](/close "wikilink")`;`
` `
`OnFull:`
`   `[`npctalk`](/npctalk "wikilink")` "There are too many cool people here!";`
`   `[`warpwaitingpc`](/warpwaitingpc "wikilink")` "prontera",150,170;`
`   `[`disablewaitingroomevent`](/disablewaitingroomevent "wikilink")` "WaitingNPC";`
`   `[`delwaitingroom`](/delwaitingroom "wikilink")` "WaitingNPC";`
`   set $@npcWaitingRoom, 0;`
`   `[`end`](/end "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")