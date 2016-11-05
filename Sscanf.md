---
title: Sscanf
permalink: /Sscanf/
---

Syntax
------

-   [sscanf](/sscanf "wikilink")(<string>,<format>\[,param\[,param\[,...\]\]\])

Description
-----------

[C style sscanf](/wikibooks:C++_Programming/Code/Standard_C_Library/Functions/scanf "wikilink"). All C format specifiers are supported. More info: sscanf @ www.cplusplus.com. The number of params is only limited by the Athena script engine.

Examples
--------

[`sscanf`](/sscanf "wikilink")`("This is a test: 42 foobar", "This is a test: %d %s", .@num, .@str$);`
[`dispbottom`](/dispbottom "wikilink")` .@num + " " + .@str$; // "42 foobar"`

[Category:Script Command](/Category:Script_Command "wikilink")