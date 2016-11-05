---
title: Setbattleflag
permalink: /Setbattleflag/
---

Syntax
------

-   [setbattleflag](/setbattleflag "wikilink") "<battle flag>",<value>;
-   [getbattleflag](/getbattleflag "wikilink")("<battle flag>")

Description
-----------

Sets or gets the value of the given battle flag. Battle flags are the flags found in the battle/\*.conf files and is also used in Lupus' variable rates script.

Examples
--------

`// Will set the base experience rate to 20x (2000%)`
`   `[`setbattleflag`](/setbattleflag "wikilink")` "base_exp_rate",2000;`
`   `
`// Will return the value of the base experience rate (when used after the above example, it would print 2000).`
`   `[`mes`](/mes "wikilink")` `[`getbattleflag`](/getbattleflag "wikilink")`("base_exp_rate");`

[Category:Script Command](/Category:Script_Command "wikilink")