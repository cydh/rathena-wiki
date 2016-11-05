---
title: Close2
permalink: /Close2/
---

Syntax
------

-   **close2**;

Description
-----------

This command will create a 'close' button in the message window for the invoking character. This is one of the ways to end a speech from an [NPC](/NPC "wikilink"). Once the button is clicked, the message box will disappear, but unlike [close](/close "wikilink") the script execution will continue. So after a close2 command an [end](/end "wikilink") command must follow to terminate the script. If no window is currently on screen, the [invoking character](/RID "wikilink") will get stuck in the NPC.

Examples
--------

[`mes`](/mes "wikilink")` "[Woman]";`
`mes "I am finished talking to you, click the close button.";`
`close2;`
[`dispbottom`](/dispbottom "wikilink")` "This will be shown at the characters chat window.";`
[`end`](/end "wikilink")`;`

`mes "Thank you for using";`
`mes "the Kafra Services.";`
`close2;`
[`cutin`](/cutin "wikilink")` "", 255;`
`end;`

Probably the most common usage of this command. Removing a previously set cutin, after the NPC dialog is closed.

[Category:Script Command](/Category:Script_Command "wikilink")