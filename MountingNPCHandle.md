---
title: MountingNPCHandle
permalink: /MountingNPCHandle/
---

New Mounts : NPC Scripting Support
==================================

This page is a short explanation of the available functions to handle **New Mounts**.

### ismounting()

This allows you to check if the player is riding a new mount. Here's an example on how to use **ismounting**:

[`if`](/if "wikilink")`( `**`ismounting`**`() )`
`   `[`dispbottom`](/dispbottom "wikilink")` "You are riding a new mount!";`
[`else`](/else "wikilink")
`   dispbottom "You are not riding a new mount";`

### setmounting()

This allows you to set a player to ride a new mount. You have to remember these things when setting it on an actual script:

-   It returns 1 on success and 0 when the target is not able to mount (i.e. due to it riding something else such as a peco, dragon, etc.)
-   It will release the target's mount if already riding a new mount.

Below is an example with conjunction of **ismounting()**:

`if( ismounting() ) {`
`   mes "You are riding a new mount";`
`   `**`setmounting`**`();//This removes the user mount`
`} else {`
`   //attempts to mount the user`
`   if( `**`setmounting`**`() ) { `
`       mes "You are now riding a new mount! Enjoy";`
`   } else { //Mounting didn't worked (i.e. The character is already mounting something else `
`such as a peco, dragon, wug, mado gear, etc.)`
`       mes "You are already mounted a ride.";`
`   }`
`}`
[`close`](/close "wikilink")`;`

Changelog
---------

-   [r15009](http://sourceforge.net/apps/trac/rathena/changeset/15009) Added from RREMu.

[Category:Script Command](/Category:Script_Command "wikilink")