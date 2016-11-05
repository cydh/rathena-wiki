---
title: Completequest
permalink: /Completequest/
---

Syntax
------

-   **completequest** <ID>;

Description
-----------

Change the state for the given quest <ID> to "complete" and remove from the users quest log.

Examples
--------

This is an excerpt from

[`jobchange`](/jobchange "wikilink")` `[`roclass`](/roclass "wikilink")`(`[`eaclass`](/eaclass "wikilink")`()|`[`EAJL_THIRD`](/Variables#Constants "wikilink")`);`
`   `[`set`](/set "wikilink")` `[`JobLevel`](/Variables#Parameter_Constants "wikilink")`, 1;`
`   `[`nude`](/nude "wikilink")`;`
`   `[`getitem`](/getitem "wikilink")` 6121,1;`
`   getitem 6122,1;`
`   getitem 2795,1;`
`   getitem 5750,1;`
`   `[`delitem`](/delitem "wikilink")` 6269,1;`
`   `[`mes`](/mes "wikilink")` "[Dumk]";`
`   mes "Congratulations.";`
`   mes "Welcome to your new life.";`
`   `**`completequest`**` 7180; `**`//Sets` `quest` `7180` `to` `complete,` `then` `removes` `it` `from` `the` `quest` `log.`**
`   `[`set`](/set "wikilink")` job_sha,28;`
`   `[`next`](/next "wikilink")`;`
`   mes "[Dumk]";`
`   mes "It's a fashionable uniform.";`
`   mes "It uses patterns of leopard and feathers.";`
`   mes "The fashion world will be shocked.";`
`   next;`

[Category:Script_Command](/Category:Script_Command "wikilink")