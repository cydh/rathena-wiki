---
title: Detachnpctimer
permalink: /Detachnpctimer/
---

Syntax
------

-   [detachnpctimer](/detachnpctimer "wikilink") {"<NPC name>"};

Description
-----------

Use to remove the RID attached to an NPC used by "[attachnpctimer](/attachnpctimer "wikilink") {"<character name>"};" You can only use this when the NPC Timer is not running, use "stopnpctimer" to stop the NPC Timer.

Examples
--------

<NPC Header>` {`
`   // We need to use attachnpctimer because the mes command below needs RID attach`
`   `[`attachnpctimer`](/attachnpctimer "wikilink")`;`
`   `[`initnpctimer`](/initnpctimer "wikilink")`;`
`   `[`npctalk`](/npctalk "wikilink")` "I cant talk right now, give me 10 seconds";`
`   `[`end`](/end "wikilink")`;`
[`OnTimer`](/OnTimer "wikilink")`5000:`
`   npctalk "Ok 5 seconds more";`
`   end;`
`OnTimer6000:`
`   npctalk "4";`
`   end;`
`OnTimer7000:`
`   npctalk "3";`
`   end;`
`OnTimer8000:`
`   npctalk "2";`
`   end;`
`OnTimer9000:`
`   npctalk "1";`
`   end;`
`OnTimer10000:`
`   `[`stopnpctimer`](/stopnpctimer "wikilink")`;`
`   mes "[Man]";`
`   mes "Ok we can talk now";`
`   `[`detachnpctimer`](/detachnpctimer "wikilink")`;`
`   // and remember attachnpctimer and detachnpctimer can only use while the NPC timer is not running !`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")