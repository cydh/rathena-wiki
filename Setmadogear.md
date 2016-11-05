---
title: Setmadogear
permalink: /Setmadogear/
---

[Category:Script Command](/Category:Script_Command "wikilink")

Syntax
------

-   **checkmadogear**()
-   **setmadogear** {<flag>};

Description
-----------

### checkmadogear

This allows you to check if the character has already mounted a Mado.

### setmadogear

If <flag> is set to 0, this command will remove the mount from the character. Otherwise it gives the invoking character a Mado (if they are a Mechanic).

The accompanying function will return 1 if the invoking character has a Mado and 0 if they don't.

Example
-------

Here are some sample scripts which might be a help to you:

### checkmadogear Sample

`if( checkmadogear() )`
`        dispbottom "You are already mounted a Mado!";`
`else`
`        dispbottom "You don't have Mado";`

### setmadogear Sample

`if( checkdmadogear() ) {`
`     mes "You are already mounting";`
`     close;`
`  } else { `
`          setmadogear;`
`  }`

You can check as well the official rAthena Universal NPC ([trunk/npc/custom/breeder.txt](https://rathena.svn.sourceforge.net/svnroot/rathena/trunk/npc/custom/breeder.txt)) as a reference.