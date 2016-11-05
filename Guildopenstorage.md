---
title: Guildopenstorage
permalink: /Guildopenstorage/
---

Syntax
------

-   [guildopenstorage](/guildopenstorage "wikilink")();

Description
-----------

This function works the same as '[openstorage](/openstorage "wikilink")' but will open a guild storage window instead for the guild storage of the guild the invoking character belongs to. This is a function because it returns a value - 0 if the guild storage was opened successfully and 1 if it wasn't. (Notice, it's a ZERO upon success.) Since guild storage is only accessible to one character at one time, it may fail if another character is accessing the guild storage at the same time.

This will also fail and return 2 if the character does not belong to any guild.

Example
-------

`if (`[`guildopenstorage`](/guildopenstorage "wikilink")`() == 1) {`
`   `[`mes`](/mes "wikilink")` "[Kafra Employee]";`
`   mes "I'm sorry but another guild member is using the guild storage";`
`   mes "right now.  Please wait until that person is finished.";`
`   `[`close2`](/close2 "wikilink")`;`
`   `[`cutin`](/cutin "wikilink")` "", 255;`
`   `[`end`](/end "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")