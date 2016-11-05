---
title: Progressbar
permalink: /Progressbar/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   progressbar "<color>",<seconds>;

Description
-----------

This command works almost like '[sleep2](/Sleep2 "wikilink")', but displays a progress bar above the head of the currently attached character (like cast bar). Once the given amount of seconds passes, the script resumes.

If the character moves while the progress bar progresses, it is aborted and the script ends. The color format is in RGB (0xRRGGBB). The color is currently ignored by the client and appears always green.

Example
-------

Here is a sample script which might be a help to you:

`mes "This will show the progressbar for 10 seconds.";`
`close2;`
`progressbar "green",10;`
`end;`