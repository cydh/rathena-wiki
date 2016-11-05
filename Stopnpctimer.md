---
title: Stopnpctimer
permalink: /Stopnpctimer/
---

Syntax
------

-   **stopnpctimer** {<attach flag>};
-   **stopnpctimer** {"<NPC name>"};
-   **stopnpctimer** {"<NPC name>"{, <attach flag>}};

Description
-----------

This script command acts as a partner to the [initnpctimer](/initnpctimer "wikilink") and [startnpctimer](/startnpctimer "wikilink") script commands. When called, it will stop any active NPC timer from ticking but will not reset the tick value to 0. When [startnpctimer](/startnpctimer "wikilink") is called after this command, the timer will resume from the tick that it was stopped at.

Syntax
------

See [initnpctimer](/initnpctimer#Parameters "wikilink").

Examples
--------

-   Stop an NPC timer after 30 seconds of processing.

[`OnInit`](/OnInit "wikilink")`:`
`    `[`initnpctimer`](/Initnpctimer "wikilink")`;`
`    `[`end`](/End "wikilink")`;`
[`OnTimer`](/OnTimer "wikilink")`30000:`
`    `[`announce`](/Announce "wikilink")` "30 seconds has expired.", bc_all|bc_npc;`
`    stopnpctimer;`
`    end;`

[Category:Script Command](/Category:Script_Command "wikilink")