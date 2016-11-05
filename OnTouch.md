---
title: OnTouch
permalink: /OnTouch/
---

Syntax
------

`Map,X,Y,facing script  NPCName ID,OnTouch_X,OnTouchY,{`
`OnTouch:`

Description
-----------

OnTouch is rather hard to explain. In the beginning of the script you specify the area that when the player enters that specified area, the following script is executed. You cannot specify a specific area. If you do 3,3 if the player enters any 3 squares around the NPC, the script is executed.

**Trick**: Using "end;" at the beginning of the script stops players from executing the script by clicking on the NPC, so they can only execute it if they walk into the specified area.

Example
-------

`prontera,147,153,3 script  Mary    71,3,3,{`
`   end;`
`OnTouch:`
`   mes "[Mary]";`
`   mes "Have you seen my lamb?";`
`   close;`
`   }`

[Category:Script Command](/Category:Script_Command "wikilink")