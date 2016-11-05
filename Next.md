---
title: Next
permalink: /Next/
---

Syntax
------

-   **next**;

Description
-----------

This command will display a 'next' button in the message window for the invoking character. Clicking on it will cause the window to clear and display a new one. Used to segment NPC-talking, next is often used in combination with [mes](/mes "wikilink") and [close](/close "wikilink").

If no window is currently on screen, one will be created, but once the invoking character clicks on it, a warning is thrown on the server console and the script will terminate.

Example
-------

[`mes`](/mes "wikilink")` "[Example]";`
`mes "Hello, I'm an example!";`
`mes "Click the next button to see the rest of the text";`
**`next`**`; //This will display the button.`
`mes "[Example]";`
`mes "This is the rest of the text";`
[`close`](/close "wikilink")`; //Closes the window and ends the script.`

[Category:Script_Command](/Category:Script_Command "wikilink")