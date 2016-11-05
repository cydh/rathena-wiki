---
title: Is clientver
permalink: /Is_clientver/
---

Syntax
------

-   **is_clientver**(<type>,<value>{,<char id>})

Description
-----------

Checks a character's client version against a specified value. If no char id is given, the command will run for the invoking character. The function will return 1 if the player's version is greater than or equal to the value, and 0 otherwise.

Available types are:

`0 - version number (packet_db_ver)`
`1 - client date (YYYYMMDD)`

[Category:Script Command](/Category:Script_Command "wikilink")