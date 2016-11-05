---
title: Getmapxy
permalink: /Getmapxy/
---

Syntax
------

-   **getmapxy**("<variable for map name>",<variable for x>,<variable for y>,<type>{,"<search string>"});

Description
-----------

This function will locate a character object, [NPC](/NPC "wikilink") object or pet's coordinates and place their coordinates into the variables specified when calling it. It will return 0 if the search was successful, and -1 if the parameters given were not variables or the search was not successful.

Type is the type of object to search for:

| Value | Description      |
|-------|------------------|
| 0     | Character object |
| 1     | NPC object       |
| 2     | Pet object       |
| 3     | Monster object   |

While 3 is meant to look for a monster object, no searching will be done if you specify type 3, and the function will always return -1.

The search string is optional. If it is not specified, the location of the invoking character will always be returned for types 0 and 2, the location of the NPC running this function for type 1. If a search string is specified, for types 0 and 1, the character or NPC with the specified name will be located. If type is 3, the search will locate the current pet of the character who's name is given in the search string, it will NOT locate a pet by name.

Examples
--------

`prontera,164,301,3 script  Meh 730,{`
`   `[`mes`](/mes "wikilink")` "My name is Meh. I'm here so that Nyah can find me.";`
`   `[`close`](/close "wikilink")`;`
`}`
`prontera,164,299,3 script  Nyah    730,{`
`   mes "My name is Nyah.";`
`   mes "I will now search for Meh all across the world!";`
`   if (`**`getmapxy`**`(@mapname$,@mapx,@mapy,1,"Meh")!=0) goto Notfound;`
`   mes "And I found him on map "+@mapname$+" at X:"+@mapx+" Y:"+@mapy+" !";`
`   close;`
`Notfound:`
`   mes "I can't seem to find Meh anywhere!";`
`   close;`
`}`

Notice that NPC objects disabled with '[disablenpc](/disablenpc "wikilink")' will still be located.

[Category:Script Command](/Category:Script_Command "wikilink")