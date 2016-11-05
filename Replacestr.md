---
title: Replacestr
permalink: /Replacestr/
---

Syntax
------

-   [replacestr](/replacestr "wikilink")(<input>, <search>, <replace>{, <usecase>{, <count>}})

Description
-----------

Replaces all instances of a search string in the input with the specified replacement string. By default is case sensitive unless <usecase> is set to 0. If specified it will only replace as many instances as specified in the count parameter.

Examples
--------

[`replacestr`](/replacestr "wikilink")`("testing tester", "test", "dash"); //returns "dashing dasher"`
[`replacestr`](/replacestr "wikilink")`("Donkey", "don", "mon", 0); //returns "monkey"`
[`replacestr`](/replacestr "wikilink")`("test test test test test", "test", "yay", 0, 3); //returns "yay yay yay test test"`

[Category:Script Command](/Category:Script_Command "wikilink")