---
title: Strmobinfo
permalink: /Strmobinfo/
---

Syntax
------

-   **strmobinfo**(<type>,<monster id>);

Description
-----------

This function will return information about a [monster](/mob "wikilink") record in the database, as per . Type is the kind of information returned:

| Value | Description                                      |
|-------|--------------------------------------------------|
| 1     | 'english name' field in the database, a string.  |
| 2     | 'japanese name' field in the database, a string. |
| 3     | Level.                                           |
| 4     | Maximum HP.                                      |
| 5     | Maximum SP.                                      |
| 6     | Experience reward.                               |
| 7     | Job experience reward.                           |

Examples
--------

[`mes`](/mes "wikilink")` `**`strmobinfo`**`(1,1002); // Poring`

[Category:Script_Command](/Category:Script_Command "wikilink")