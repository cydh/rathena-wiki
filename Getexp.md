---
title: Getexp
permalink: /Getexp/
---

Syntax
------

-   [getexp](/getexp "wikilink") <base exp>,<job exp>;

Description
-----------

This command will give the invoking character a specified number of base and job experience points. Can be used as a quest reward. Negative values won't work.

Note that 'getexp' is subject to the **'quest_exp_rate**' config option, which adjusts the gained value. If you want to bypass this, use the 'set' method.

Examples
--------

`// get 10,000 base exp and 5,000 job exp`
`getexp 10000,5000;`

You can also use the "set" command with the constants defined in 'db/const.txt':

`// These 2 combined has the same effect as the first example`
`set BaseExp, BaseExp+10000;`
`set JobExp, JobExp+5000;`

You can also reduce the amount of experience points:

`set BaseExp,BaseExp-10000;`

[Category:Script Command](/Category:Script_Command "wikilink")