---
title: Bindatcmd
permalink: /Bindatcmd/
---

Syntax
------

-   [bindatcmd](/bindatcmd "wikilink") "command","<NPC object name>::<event label>"{,<atcommand level>,<charcommand level>};

Description
-----------

This command will bind a NPC event label to an [atcommand](/atcommand "wikilink"). Upon execution of the atcommand, the user will invoke the NPC event label. Each atcommand is only allowed one binding. If you rebind, it will override the original binding.

The following variables are created upon execution:

-   .@atcmd_command$: The atcmd used.
-   .@atcmd_numparameters: The number of parameters defined.
-   .@atcmd_parameters$\[\]: Array containing the given parameters, starting from an index of 0.

Example
-------

When a user types the command "@test", an angel effect will be shown.

`-  `[`script`](/Basic_Scripting#NPC "wikilink")` atcmd_example   -1,{`
[`OnInit`](/OnInit "wikilink")`:`
`   `[`bindatcmd`](/bindatcmd "wikilink")` "test",`[`strnpcinfo`](/strnpcinfo "wikilink")`(3)+"::OnAtcommand";`
`   `[`end`](/end "wikilink")`;`
`OnAtcommand:`
`   `[`specialeffect2`](/specialeffect2 "wikilink")` 338;`
`   end;`
`}`

For another good usage example of this command, see [changelook](/changelook "wikilink").

See Also
--------

-   [unbindatcmd](/unbindatcmd "wikilink")
-   [useatcmd](/useatcmd "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")