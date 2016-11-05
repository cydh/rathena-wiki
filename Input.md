---
title: Input
permalink: /Input/
---

Syntax
------

-   **input** <variable>\[, <min value>\[, <max value>\]\];
-   **input**(<variable>\[, <min value>\[, <max value>\]\]);

Description
-----------

This command will make an input box pop up on the client connected to the [invoking character](/RID#Usage "wikilink"), to allow entering of a string or digits only, depending on variable's type.

Normally you cannot input a negative number with this command, to prevent exploits in badly written scripts, which would let people, for example, put negative amounts of [Zeny](/Zeny "wikilink") into a bank script and receive free Zeny as result. The default values for *min value* and *max value* are specified as *input_min_value* and *input_max_value* respectively in **conf/script_athena.conf**.

Since r12192 (Trunk) and r12302 (Stable) the command has two additional optional arguments and a return value to safely override this behavior, when required. Depending on used variable type the min and max values, and the return value have different meaning:

-   For **strings** min and max specify the minimum and maximum string length. The return value is -1, if the string was too short, 1, if it was too long, otherwise 0.
-   For **numbers** min and max specify the minimum and maximum value, the variable is allowed to be set to. If the entered value is outside the specified range \[min,max\], it is capped to the nearest valid value. The return value is -1 for too small values, 1 for too large values, otherwise 0.

Examples
--------

[`mes`](/mes "wikilink")` "[Woman]";`
`mes "Try and guess the number I am thinking of.";`
`mes "The number will be between 1 and 10.";`
[`next`](/next "wikilink")`;`
[`set`](/set "wikilink")` .@number, `[`rand`](/rand "wikilink")`(1, 10);`
[`while`](/while "wikilink")`(input(.@guess, 1, 10))`
`{`
`    mes "[Woman]";`
`    mes "Didn't you listen before? The number is between 1 and 10.";`
`    next;`
`}`
`mes "[Woman]";`
[`if`](/if "wikilink")`(.@guess==.@number)`
`{`
`    mes "Well done, that was the number I was thinking of.";`
`}`
`else`
`{`
`    mes "Sorry, that wasn't the number I was thinking of.";`
`}`
[`close`](/close "wikilink")`;`

`mes "[Man]";`
`mes "You need a password to pass.";`
`next;`
`input .@pwd$;`
`if(.@pwd$!="s3cr3t")`
`{`
`    mes "[Man]";`
`    mes "Get out.";`
`    close;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")