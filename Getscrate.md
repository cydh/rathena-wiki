---
title: Getscrate
permalink: /Getscrate/
---

Syntax
------

-   [getscrate](/getscrate "wikilink")(<effect type>,<base rate>{,<target ID number>})

Description
-----------

This function will return the chance of a status effect affecting the invoking character, in percent, modified by the their current defense against said status. The 'base rate' is the base chance of the status effect being inflicted, in percent.

You can see the full list of available effect types you can possibly inflict in under **Eff_**

Example
-------

`if (rand(100) > getscrate(Eff_Blind, 50)) goto BlindHimNow;`

[Category:Script Command](/Category:Script_Command "wikilink")