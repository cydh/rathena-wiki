---
title: Getvariableofnpc
permalink: /Getvariableofnpc/
---

Syntax
------

-   **getvariableofnpc**(<variable>, &lt;"npc name"&gt;);

Description
-----------

This function retrieves a variable reference to a [permanent NPC variable](/Variables#NPC_Variables "wikilink") in an another NPC script. Note, that the return value behaves like a variable, not like a value, which means, the return value of this function can be used in other script commands, which expect a variable as parameter.

Examples
--------

[`mes`](/mes "wikilink")` "The current name of my co-worker is "+getvariableofnpc(.npcname$, "Site Co-Worker");`

Prints the value of the variable *.npcname$* as if it was used inside the NPC "Site Co-Worker".

`mes "Let's give him an another name...";`
[`set`](/set "wikilink")` getvariableofnpc(.npcname$, "Site Co-Worker"), "Sleeping Tom";`

Sets the variable *.npcname$* of the NPC "Site Co-Worker" to "Sleeping Tom".

`set .mynpcnamecopy$, getvariableofnpc(.npcname$, "Site Co-Worker");`
`set .mynpcnamecopy$, "Sleeping Tom";`

Will change the variable *.mynpcnamecopy$* to "Sleeping Tom", but keep the variable *.npcname$* of NPC "Site Co-Worker" unaffected, because the first call to set copies the value of *.npcname$* to *.mynpcnamecopy$*, rather than the reference.

[Category:Script Command](/Category:Script_Command "wikilink")