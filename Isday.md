---
title: Isday
permalink: /Isday/
---

Syntax
------

-   **isday**();
-   **isnight**();

Description
-----------

These functions determine whether server day or night cycle is currently in effect or not. If the server night is in effect, isday and isnight will return 0 and 1, otherwise 1 and 0 respectively.

Examples
--------

[`if`](/if "wikilink")`(!isday())`
`{`
`    `[`mes`](/mes "wikilink")` "I do not work at night, come again tomorrow.";`
`    `[`close`](/close "wikilink")`;`
`}`

`if(isnight())`
`{`
`    mes "I do not work at night, come again tomorrow.";`
`    close;`
`}`

These two script fragments achieve the same effect.

[Category:Script Command](/Category:Script_Command "wikilink")