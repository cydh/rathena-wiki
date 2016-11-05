---
title: Compare
permalink: /Compare/
---

Syntax
------

-   [compare](/compare "wikilink")(<string>,<substring>);

Description
-----------

This command compares 2 strings and returns if the substring is in the main string or not. This command is not case sensitive.

Return Values
-------------

| Value | Description                              |
|-------|------------------------------------------|
| 0     | The substring is not in the main string. |
| 1     | The substring is in the main string.     |

Examples
--------

`// dothis; will be executed ('Bloody Murderer' contains 'Blood').`
`   if (compare("Bloody Murderer","Blood"))`
`       dothis;`
`// dothat; will not be executed ('Blood Butterfly' does not contain 'Bloody').`
`   if (compare("Blood Butterfly","Bloody"))`
`       dothat;`

[Category:Script Command](/Category:Script_Command "wikilink")