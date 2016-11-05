---
title: Msg txt
permalink: /Msg_txt/
---

Syntax
------

`char* `**`msg_txt`**`(int msg_number);`

Parameters
----------

-   **msg_number** - Message ID of the requested message.

Description
-----------

This function retrieves a pointer to a message string, which was loaded from **msg_athena.conf**. Although the return value is not typed as **const**, it should be handled as such and the contents pointed to by the pointer should be only read.

Example
-------

[`clif_displaymessage`](/clif_displaymessage "wikilink")`(sd->fd, msg_txt(3));`

This would pass pointer to the message "Character not found." to the function clif_displaymessage.

[Category:Source Functions](/Category:Source_Functions "wikilink")