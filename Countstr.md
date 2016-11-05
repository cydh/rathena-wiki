---
title: Countstr
permalink: /Countstr/
---

Syntax
------

-   [countstr](/countstr "wikilink")(<input>, <search>{, <usecase>})

Description
-----------

Counts all instances of a search string in the input. By default is case sensitive unless <usecase> is set to 0.

Examples
--------

[`countstr`](/countstr "wikilink")`("test test test Test", "test"); //returns 3`
[`countstr`](/countstr "wikilink")`("cake Cake", "Cake", 0); //returns 2`

[Category:Script Command](/Category:Script_Command "wikilink")