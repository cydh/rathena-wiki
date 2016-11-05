---
title: Clif Authfail
permalink: /Clif_Authfail/
---

Syntax
------

`int `**`clif_authfail_fd`**`(int fd, int type);`

Parameters
----------

-   **fd** - Socket descriptor (connection handle) of the connection to disconnect.
-   **type** - Indicates, which message should be displayed on the client upon disconnection.
    -   1 - Server closed.
    -   2 - Someone already logged into this ID.
    -   3 - You've been disconnected due to a time delay between you and the server.
    -   4 - Server is jammed due to over population. Please try again shortly.
    -   5 - You are under-aged.
    -   8 - Server still recognizes your last log-in. Please try again after a few minutes.
    -   9 - IP capacity of this Internet Cafe is full. Would you like to pay the personal base?
    -   10 - You are out of available time paid for. Game will be shut down automatically.
    -   15 - You have been forced to disconnect by the Game Master Team.
    -   other - Disconnected from the server.

Description
-----------

Notifies the client, that it is about being disconnected, usually due to authentication failure (thus the name). Causes the client to disconnect and display a message box depending on type.

Example
-------

`clif_authfail_fd(sd->fd, 15);`

This would disconnect the player session and notify the player, that he or she has been kicked by a GM.

[Category:Source_Functions](/Category:Source_Functions "wikilink")