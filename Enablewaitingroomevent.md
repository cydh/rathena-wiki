---
title: Enablewaitingroomevent
permalink: /Enablewaitingroomevent/
---

Syntax
------

-   **enablewaitingroomevent** {&lt;"npc name"&gt;};
-   **disablewaitingroomevent** {&lt;"npc name"&gt;};
-   **enablearena**;
-   **disablearena**;

Description
-----------

These commands will enable and disable triggering the waiting room event respectively. Optionally, giving an [NPC](/NPC "wikilink") name will do that for a specified NPC, rather than the current one. The chat room will not disappear when triggering is disabled and enabled in this manner and players will not be kicked out of it. Enabling a chat room event will also cause it to immediately check whether the number of users in it exceeded the trigger amount and trigger the event accordingly.

Commands **enablearena** and **disablearena** are parameter-less aliases, which might have been introduced for sake of compatibility with official [AEGIS](/AEGIS "wikilink") scripts.

Examples
--------

[`OnInit`](/OnInit "wikilink")`:`
`    `[`waitingroom`](/waitingroom "wikilink")` "Merchant Area", 1, "OnWarpToArea";`
`    `[`end`](/end "wikilink")`;`
`OnWarpToArea:`
`    `[`warp`](/warp "wikilink")` "merchant", 0, 0;`
`    end;`
`OnClock1900:`
`    disablewaitingroomevent;`
`    end;`
`OnClock2000:`
`    enablewaitingroomevent;`
`    end;`

This would disable warping to the merchant area from 7.00pm to 8.00pm (ex. restricting deals during [WoE](/WoE "wikilink")).

[Category:Script Command](/Category:Script_Command "wikilink")