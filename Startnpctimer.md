---
title: Startnpctimer
permalink: /Startnpctimer/
---

Syntax
------

-   [startnpctimer](/startnpctimer "wikilink") {<attach flag>};
-   [startnpctimer](/startnpctimer "wikilink") {"<NPC name>"};
-   [startnpctimer](/startnpctimer "wikilink") {"<NPC name>"{, <attach flag>}};

Description
-----------

This script command works almost exactly like [initnpctimer](/initnpctimer "wikilink"), however calling this method does not reset the timer for the NPC. When called, it will resume the timer if it has been stopped using [stopnpctimer](/stopnpctimer "wikilink"), and it will not reset the NPC timer tick to 0.

Parameters
----------

See [initnpctimer](/initnpctimer#Parameters "wikilink").

Examples
--------

-   Start or stop an NPC timer using menus.

[`switch`](/switch "wikilink")`( select("Resume timer", "Stop timer") )`
`{`
`    `[`case`](/case "wikilink")` 1:`
`         startnpctimer;`
`         `[`end`](/end "wikilink")`;`
`    case 2:`
`         stopnpctimer;`
`         end;`
`}`
[`OnTimer`](/OnTimer "wikilink")`60000:`
`    `[`announce`](/announce "wikilink")` "This will only ever be called once.", bc_all|bc_npc;`
`    end;`

[Category:Script Command](/Category:Script_Command "wikilink")