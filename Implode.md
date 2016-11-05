---
title: Implode
permalink: /Implode/
---

Syntax
------

-   [implode](/implode "wikilink")(<string_array>{,<glue>})

Description
-----------

Combines all substrings within the specified string array into a single string. If the glue parameter is specified, it will be inserted in between each substring.

Examples
--------

[`setarray`](/setarray "wikilink")` .@my_array$[0], "This", "is", "a", "test";`
[`implode`](/implode "wikilink")`(.@my_array$, " "); //returns "This is a test"`

[Category:Script Command](/Category:Script_Command "wikilink")