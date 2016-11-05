---
title: Return
permalink: /Return/
---

Syntax
------

-   **return** \[<return value>\];

Description
-----------

This command causes the script execution to leave previously called function with [callfunc](/callfunc "wikilink") or script with [callsub](/callsub "wikilink") and return to the location, where the call originated from. Optionally a return value can be supplied, when the call was done using the function form.

Using this command outside of functions or scripts referenced by callsub will result in error and termination of the script.

Examples
--------

`    `[`set`](/set "wikilink")` .@var,`[`callsub`](/callsub "wikilink")`(L_myAddition,.@a_val,.@b_val);`
`    `[`mes`](/mes "wikilink")` "The result is "+.@var+".";`
`    `[`close`](/close "wikilink")`;`
`L_myAddition:`
`    return `[`getarg`](/getarg "wikilink")`(0)+getarg(1);`

`    set .@var,`[`callfunc`](/callfunc "wikilink")`("MyAddition",.@a_val,.@b_val);`
`    mes "The result is "+.@var+".";`
`    close;`
`    ...`
`function   script  MyAddition  {`
`    return getarg(0)+getarg(1);`
`}`

Assuming .@a_val and .@b_val being 1, both examples would yield a message displaying, that the result is 2.

`    mes "Oh no...";`
`    `[`close2`](/close2 "wikilink")`;`
`    callsub L_scream;`
`    `[`end`](/end "wikilink")`;`
`L_scream:`
`    `[`npctalk`](/npctalk "wikilink")` "Iiiiiiiiiiiiieeeeeeeeeeeeeeeeeeeeeeeeek!!!";`
`    return;`

[Category:Script Command](/Category:Script_Command "wikilink")