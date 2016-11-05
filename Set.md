---
title: Set
permalink: /Set/
---

As of the usage of [set](/set "wikilink") has become obsolete and is no longer a requirement.

Syntax
------

-   [set](/set "wikilink") <variable>,<expression>;
-   [set](/set "wikilink")(<variable>,<expression>)
-   <variable> = <expression>;

Description
-----------

This command will set a variable to the value that the expression results in.
This is the most basic script command and is used a lot whenever you try to do anything more advanced than just printing text into a message box.

Returns the variable reference (since trunk ).

Examples
--------

[`set`](/set "wikilink")` .@x,100;  // will make .@x equal 100.`
[`set`](/set "wikilink")` .@x,1+5/8+9;  // will compute 1+5/8+9 (which is, surprisingly, 10 - remember, all numbers are integer in this language) and make .@x equal it.`

or

`.@x = 100;  // will make .@x equal 100.`
`.@x = 1+5/8+9;  // will compute 1+5/8+9 (which is, surprisingly, 10 - remember, all numbers are integer in this language) and make .@x equal it.`

For more information read: [r15982: Script Engine Update](http://rathena.org/board/topic/62395-r15982-script-engine-update/)

[Category:Script Command](/Category:Script_Command "wikilink")