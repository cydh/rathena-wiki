---
title: Getequipisequiped
permalink: /Getequipisequiped/
---

Syntax
------

-   [getequipisequiped](/getequipisequiped "wikilink")(<equipment slot>)

Description
-----------

This functions will return 1 if there is an equipment placed on the specified equipment slot and 0 otherwise. For a list of equipment slots see '[getequipid](/getequipid "wikilink")'. Function originally used by the refining NPCs:

Examples
--------

`if (`[`getequipisequiped`](/getequipisequiped "wikilink")`(EQI_HEAD_TOP)) goto L_equipped;`
`   `[`mes`](/mes "wikilink")` "[Refiner]";`
`   mes "Do you want me to refine your dumb head?";`
`   mes "I mean hat?";`
`   `[`close`](/close "wikilink")`;`
`L_equipped:`
`   mes "[Refiner]";`
`   mes "That's a fine hat you are wearing there...";`
`   close;`

[Category:Script Command](/Category:Script_Command "wikilink")