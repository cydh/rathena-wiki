---
title: Freeloop
permalink: /Freeloop/
---

Syntax
------

-   [freeloop](/freeloop "wikilink")({<toggle>})

Description
-----------

Toggling this to enabled (1) allows the script instance to bypass the infinite loop protection, allowing your script to loop as much as it may need. Disabling (0) will warn you if an infinite loop is detected.

The command will return the state of freeloop for the attached script, even if no argument is provided.

Examples
--------

[`freeloop`](/freeloop "wikilink")`(1); // allow script to loop freely`
`// do your long loop stuff here`
[`freeloop`](/freeloop "wikilink")`(0); // turn infinity loop warning back on`

[Category:Script Command](/Category:Script_Command "wikilink")