---
title: Getnpctimer
permalink: /Getnpctimer/
---

Syntax
------

-   **getnpctimer**(<type of information>{,"<NPC name>"})

Description
-----------

This script command is one out of a set of commands and functions that create and manage an NPC-based timer. Specifically, 'getnpctimer' provides the timer information. See [\#Parameters](/#Parameters "wikilink") below for the type of information returned. The NPC name may be omitted, in which case the calling NPC is used as target.

Parameters
----------

Its parameter defines what type to return:

`0 - Will return the current tick count of the timer.`
`1 - Will return 1 if there are remaining "OnTimer`<ticks>`:" labels in the `
`    specified NPC waiting for execution.`
`2 - Will return the number of times the timer has triggered and will trigger`
`    an "OnTimer`<tick>`:"  label in the specified NPC.`

Examples
--------

[`mes`](/mes "wikilink")` "[Man]";`
`mes "I have been waiting "+(getnpctimer(0)/1000)+" seconds for you";`
`// we divide the timer returned by 1000 cause it will be displayed in `
`// milliseconds otherwise`
[`close`](/close "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink")