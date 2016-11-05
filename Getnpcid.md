---
title: Getnpcid
permalink: /Getnpcid/
---

Syntax
------

**getnpcid**(<type>{,"<npc name>"});

Description
-----------

Retrieves IDs of the currently invoked NPC. If a unique npc name is given, IDs of that NPC are retrieved instead. Type specifies what ID to retrieve and can be one of the following:

`0 - Unit ID (GID)`

If an invalid type is given or the NPC does not exist, return value is 0.

Examples
--------

`set @gid$,`**`getnpcid`**`(0);`
`mes "My GID is "+@n$;`
`close;`

`prontera,50,50,3   script  MyNPCNAME   123,{`
`set @gid$,`**`getnpcid`**`(0,"MyNPCNAME");`
`set @warpergid$,`**`getnpcid`**`(0,"Warper#1");`
`mes "My GID is "+@n$;`
`mes "The Warper's NPC ID in Prontera is "+@warpergid$;`
`close;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")