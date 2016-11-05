---
title: While
permalink: /While/
---

Syntax
------

-   [while](/while "wikilink") (<condition>) <statement>;

Description
-----------

This is probably the simplest and most frequently used loop structure. The 'while' statement can be interpreted as "while <condition> is true, perform <statement>". It is a pretest loop, meaning the conditional expression is tested before any of the statements in the body of the loop are performed. If the condition evaluates to false, the statement(s) in the body of the loop is/are never executed. If the condition evaluates to true, the statement(s) are executed, then control transfers back to the conditional expression, which is reevaluated and the cycle continues.

Multiple statements can be grouped with { }, curly braces, just like with the 'if' statement.

Examples
--------

`while (`[`switch`](/switch "wikilink")`(`[`select`](/select "wikilink")`("Yes:No") == 2 ))`
`   `[`mes`](/mes "wikilink")` "You picked no.";`

### Multiple Statements

[`while`](/while "wikilink")` (`[`switch`](/switch "wikilink")`(select("Yes:No") == 2 )) {`
`   mes "Why did you pick no?";`
`   mes "You should pick yes instead!";`
`}`

### Counter-Controlled Loop

`set .@i, 1;`
`while (.@i <= 5) {`
`   mes "This line will print 5 times.";`
`   set .@i, .@i + 1;`
`}`

### Sentinel-Controlled Loop

`mes "Input 0 to stop";`
[`input`](/input "wikilink")` .@num;`
`while (.@num != 0) {`
`   mes "You entered " + .@num;`
`   input .@num;`
`}`
[`close`](/close "wikilink")`;`

See Also
--------

-   [Loops\#While_Loop](/Loops#While_Loop "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")