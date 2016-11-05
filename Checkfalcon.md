---
title: Checkfalcon
permalink: /Checkfalcon/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [checkfalcon](/checkfalcon "wikilink")();

Description
-----------

The function will return 1 if the invoking character has a falcon and 0 if they don't.

Return Values
-------------

| Value | Description                          |
|-------|--------------------------------------|
| 0     | The character doesn't have a falcon. |
| 1     | The character has a falcon.          |

Examples
--------

        if (checkfalcon()) mes "But you already have a falcon!";