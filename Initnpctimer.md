---
title: Initnpctimer
permalink: /Initnpctimer/
---

Syntax
------

-   [initnpctimer](/initnpctimer "wikilink") {<attach flag>};
-   [initnpctimer](/initnpctimer "wikilink") {"<NPC name>"};
-   [initnpctimer](/initnpctimer "wikilink") {"<NPC name>"{, <attach flag>}};

Description
-----------

This script command will begin an NPC-attached timer on the running or specified NPC. The timer will run internally in the NPC and is not attached to any player, so will continue to run even when there are no players logged on. It is important to note that an NPC can only run a single timer on itself at any given time. In order to process multiple timers, the script would have to use player based timers such as [addtimer](/addtimer "wikilink").

The timer runs in milliseconds (1/1000th of a second) from 0, and calling this script command will begin a new timer (if a timer is not already running on the NPC) or reset the current timer on the NPC. To completely stop the NPC timer, the script command [stopnpctimer](/stopnpctimer "wikilink") must be called, and to resume the timer (without resetting the current tick) the script command [startnpctimer](/startnpctimer "wikilink") must be called.

The script can access a timer event by creating a label matching the format "OnTimer<tick>:" where the <tick> is replaced with a millisecond value to occur on. The NPC timer does not reset automatically once reaching one of these labels, therefore it is possible to multiple labels with incremented <tick> values to handle the same NPC timer (see [Examples](/#Examples "wikilink")).

Parameters
----------

### Attach Flag

The flag value determines whether a player should be directly associated with this NPC timer. When flag is specified (a value of 1) the script will attach the player who is currently attached to the script, to the timer. If no player is attached to the script when this flag is specified, then the [initnpctimer](/initnpctimer "wikilink") call will fail.

If a player is successfully attached to the NPC timer, and logs out of the game, then the event label "OnTimerQuit:" will run on the NPC (the player will still be logged in at this point) to allow cleaning up and handling of the timer.

### NPC Name

If specified, the call to [initnpctimer](/initnpctimer "wikilink") will not apply to the current running script but will take effect on the NPC which exists with the passed NPC name. If an NPC could not be found with this name then the [initnpctimer](/initnpctimer "wikilink") call will fail.

Examples
--------

-   Announce every 1 second (resetting the timer after every 1000 milliseconds)

`    initnpctimer;`
`    end;`
[`OnTimer`](/OnTimer "wikilink")`1000:`
`    `[`announce`](/announce "wikilink")` "1 second has passed!", bc_all|bc_npc;`
`    initnpctimer;`
`    `[`end`](/end "wikilink")`;`

-   Announce at 5 and 10 seconds (stopping the timer once 10000 milliseconds is reached)

`    initnpctimer;`
`    end;`
[`OnTimer`](/OnTimer "wikilink")`5000:`
`    `[`announce`](/announce "wikilink")` "5 seconds have passed!", bc_all|bc_npc;`
`    `[`end`](/end "wikilink")`;`
` OnTimer10000:`
`    announce "10 seconds have passed!!", bc_all|bc_npc;`
`    `[`stopnpctimer`](/stopnpctimer "wikilink")`;`
`    end;`

-   Perform an event on a player every 60 seconds (resetting the timer after every 60000 milliseconds)

`    initnpctimer 1;`
`    end;`
[`OnTimer`](/OnTimer "wikilink")`60000:`
`    `[`percentheal`](/percentheal "wikilink")` 10, 0;`
`    `[`message`](/message "wikilink")` `[`strcharinfo`](/strcharinfo "wikilink")`(0), "You were healed 10% HP!";`
`    initnpctimer 1;`
`    `[`end`](/end "wikilink")`;`
`OnTimerQuit:`
`    `[`stopnpctimer`](/stopnpctimer "wikilink")`;`
`    `[`end`](/end "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink")