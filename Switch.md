---
title: Switch
permalink: /Switch/
---

Syntax
------

-   [switch](/switch "wikilink")(<expression>);

Description
-----------

The switch statement is similar to a series of [if](/if "wikilink") statements on the same expression. In many occasions, you may want to compare the same variable (or expression) with many different values, and execute a different piece of code depending on which value it equals to. This is exactly what the [switch](/switch "wikilink") statement is for.

It is important to understand how the [switch](/switch "wikilink") statement is executed in order to avoid mistakes. The [switch](/switch "wikilink") statement executes line by line (actually, statement by statement). In the beginning, no code is executed. Only when a [case](/case "wikilink") statement is found with a value that matches the value of the switch expression the [case](/case "wikilink") statement(s) will to executed. The parser continues to execute the statements until the end of the [switch](/switch "wikilink") block, or the first time it sees a [break](/break "wikilink") statement. If you don't write a [break](/break "wikilink") statement at the end of a [case](/case "wikilink")'s statement list, the parser will go on executing the statements of the following [case](/case "wikilink") (fall-through).

Example
-------

`// Returns the number of refines on your top headgear`
[`set`](/set "wikilink")`(.@refCount, `[`getequiprefinerycnt`](/getequiprefinerycnt "wikilink")`(EQI_HEAD_TOP));`
`// Output a message`
[`switch`](/switch "wikilink")`(.@refCount) {`
`   // 0 means no refine yet`
`   `[`case`](/case "wikilink")` 0:`
`       `[`mes`](/mes "wikilink")`("No refine on your top headgear yet?");`
`       `[`mes`](/mes "wikilink")`("You need to go to the refiner!");`
`       `[`break`](/break "wikilink")`;`
`   // +1`
`   `[`case`](/case "wikilink")` 1:`
`       `[`mes`](/mes "wikilink")`("Your top headgear is +1!");`
`       `[`break`](/break "wikilink")`;`
`   // +2`
`   `[`case`](/case "wikilink")` 2:`
`       `[`mes`](/mes "wikilink")`("Your top headgear is +2!");`
`       `[`break`](/break "wikilink")`;`
`   // +3`
`   `[`case`](/case "wikilink")` 3:`
`       `[`mes`](/mes "wikilink")`("Your top headgear is +3!");`
`       `[`break`](/break "wikilink")`;`
`   // +4`
`   `[`case`](/case "wikilink")` 4:`
`       `[`mes`](/mes "wikilink")`("Your top headgear is +4!");`
`       // NOTE: no break here means the code from "case 5" will be executed afterwards!`
`   `
`   // +5`
`   `[`case`](/case "wikilink")` 5:`
`       `[`mes`](/mes "wikilink")`("Your top headgear is +5!");`
`       `[`break`](/break "wikilink")`;`
`   // [...]`
`   // This case will be triggered if no other case was triggered yet`
`   `[`default`](/default "wikilink")`:`
`       `[`mes`](/mes "wikilink")`("Your top headgear has upgrades above +5!");`
`       `[`break`](/break "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")