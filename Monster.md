---
title: Monster
permalink: /Monster/
---

Syntax
------

-   **monster** &lt;"map name"&gt;, <x>, <y>, &lt;"display name"&gt;, <mob id>, <amount>\[, &lt;"event label"&gt;\];

Description
-----------

This command spawns a monster at given map and coordinates, using given class and amount. Monsters spawned with this command will not re-spawn after being killed.

To address the map, on which the running [NPC](/NPC "wikilink") resides, *map name* can be set to "this". Spawning the monster on random coordinates is accomplished by setting parameters *x* and *y* to 0. The parameter *display name* specifies the in-game name of the monster, which is not necessary required to be the actual name, such as "Prontera minion". The *display name* accepts also two magic names, "--ja--" and "--en--", which are replaced by the server with the value of the kROName and iROName mob db columns of the given *mob id*, respectively. Setting the *mob id* to -1, -2 or -3 will spawn a random monster from the dead branch, poring box or bloody branch list respectively.

Optionally an *event label* can be specified, which has the form "NpcName::OnLabel" and is run upon the monster's death. If the killer was a player, [it will be attached](/RID#Usage "wikilink") to the invoked script.

Example
-------

`    `[`mes`](/mes "wikilink")` "I will spawn 5 Porings for you!";`
`    `[`close2`](/close2 "wikilink")`;`
`    monster "this",0,0,"Poring 1",1002,1,`[`strnpcinfo`](/strnpcinfo "wikilink")`(0)+"::OnPoring1Dead";`
`    monster "this",0,0,"Poring 2",1002,1,strnpcinfo(0)+"::OnPoring2Dead";`
`    monster "this",0,0,"Poring 3",1002,1,strnpcinfo(0)+"::OnPoring3Dead";`
`    monster "this",0,0,"Poring 4",1002,1,strnpcinfo(0)+"::OnPoring4Dead";`
`    monster "this",0,0,"Poring 5",1002,1,strnpcinfo(0)+"::OnPoring5Dead";`
`    `[`end`](/end "wikilink")`;`
`OnPoring1Dead:`
`    mes "You killed Poring 1";`
`    `[`close`](/close "wikilink")`;`
`OnPoring2Dead:`
`    mes "You killed Poring 2";`
`    close;`
`OnPoring3Dead:`
`    mes "You killed Poring 3";`
`    close;`
`OnPoring4Dead:`
`    mes "You killed Poring 4";`
`    close;`
`OnPoring5Dead:`
`    mes "You killed Poring 5";`
`    close;`

This will spawn 5 Porings randomly distributed on the map of the invoking character with the names "Poring 1" to "Poring 5". Each time the player kills one of them, it triggers the given event label in the NPC, which will say "You killed Poring X"

[Category:Script Command](/Category:Script_Command "wikilink")