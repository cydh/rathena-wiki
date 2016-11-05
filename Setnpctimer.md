---
title: Setnpctimer
permalink: /Setnpctimer/
---

Syntax
------

-   **setnpctimer** <tick>{,"NPC Name"};

Description
-----------

The '[setnpctimer](/setnpctimer "wikilink")' is a command that will explicitly set a NPC timer to a given tick.

Example
-------

Here is an example which will help you to understand how the **setnpctimer** command works.

[`OnTimer`](/OnTimer "wikilink")`15000:`
[`set`](/set "wikilink")` $quote,rand(5);`
[`if`](/if "wikilink")`($quote == 0) goto Lquote0;`
`if($quote == 1) `[`goto`](/goto "wikilink")` Lquote1;`
`if($quote == 2) goto Lquote2;`
`if($quote == 3) goto Lquote3;`
`if($quote == 4) goto Lquote4;`
`     Lquote0:`
`     `[`npctalk`](/npctalk "wikilink")` "If 0 is randomly picked you will see this";`
`     `**`setnpctimer`**` 0;`
`     `[`end`](/end "wikilink")`;`
`     Lquote1:`
`     npctalk "If 1 is randomly picked you will see this";`
`     `**`setnpctimer`**` 0;`
`     end;`
`     Lquote2:`
`     npctalk "If 2 is randomly picked you will see this";`
`     `**`setnpctimer`**` 0;`
`     end;`
`     Lquote3:`
`     npctalk "If 3 is randomly picked you will see this";`
`     `**`setnpctimer`**` 0;`
`     end;`
`     Lquote4: `
`     npctalk "If 4 is randomly picked you will see this";`
`     `**`setnpctimer`**` 0;`
`     end;`