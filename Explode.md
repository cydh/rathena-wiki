---
title: Explode
permalink: /Explode/
---

Syntax
------

-   [explode](/explode "wikilink")(<dest_array>,<string>,<delimiter>)

Description
-----------

Breaks a string up into substrings based on the specified delimiter. Substrings will be stored within the specified string [array](/array "wikilink"). Only the 1st char of the delimiter parameter will be used. If an empty string is passed as a delimiter, the string will be placed in the array in it's original form.

Examples
--------

[`explode`](/explode "wikilink")`(.@my_array$, "Explode:Test:1965:red:PIE", ":");`
`//.@my_array$ contents will be...`
`//.@my_array$[0]: "Explode"`
`//.@my_array$[1]: "Test"`
`//.@my_array$[2]: "1965"`
`//.@my_array$[3]: "red"`
`//.@my_array$[4]: "PIE"`

[Category:Script Command](/Category:Script_Command "wikilink")