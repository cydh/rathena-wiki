---
title: Sprintf
permalink: /Sprintf/
---

Syntax
------

-   [sprintf](/sprintf "wikilink")(<format>\[,param\[,param\[,...\]\]\])

Description
-----------

[C style sprintf](/wikibooks:C++_Programming/Code/Standard_C_Library/Functions/sprintf "wikilink"). The resulting string is returned same as in PHP. All C format specifiers are supported except %n. More info: sprintf @ www.cplusplus.com. The number of params is only limited by the Athena script engine.

Examples
--------

[`set`](/set "wikilink")` .@format$, "The %s contains %d monkeys";`
[`dispbottom`](/dispbottom "wikilink")` `[`sprintf`](/sprintf "wikilink")`(.@format$, "zoo", 5);        // "The zoo contains 5 monkeys"`
[`dispbottom`](/dispbottom "wikilink")` `[`sprintf`](/sprintf "wikilink")`(.@format$, "barrel", 82);    // "The barrel contains 82 monkeys"`

[Category:Script Command](/Category:Script_Command "wikilink")