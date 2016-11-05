---
title: Vip status
permalink: /Vip_status/
---

Syntax
------

-   **vip_status**(<type>,{"<character name>"})

Description
-----------

Returns various information about a player's VIP status.

Valid types:

`1 - VIP status. (1 if VIP, 0 if non-VIP)`
`2 - VIP expire date. (timestamp string if VIP, 0 if non-VIP)`
`3 - VIP time remaining. (timestamp string if VIP, 0 if non-VIP)`

NOTE: This command is only available if the VIP System is enabled.

Examples
--------

vip_status(1)

[Category:Script Command](/Category:Script_Command "wikilink")