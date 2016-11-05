---
title: Strpos
permalink: /Strpos/
---

Syntax
------

-   [strpos](/strpos "wikilink")(<haystack>,<needle>{,<offset>})

Description
-----------

PHP style strpos. Finds a substring (needle) within a string (haystack). The offset parameter indicates the index of the string to start searching. Returns index of substring on successful search, else -1. Comparison is case sensitive.

Examples
--------

[`strpos`](/strpos "wikilink")`("foobar", "bar", 0); //returns 3`
[`strpos`](/strpos "wikilink")`("foobarfoo", "foo", 0); //returns 0`
[`strpos`](/strpos "wikilink")`("foobarfoo", "foo", 1); //returns 6`

[Category:Script Command](/Category:Script_Command "wikilink")