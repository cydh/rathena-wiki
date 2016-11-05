---
title: Getpartnerid
permalink: /Getpartnerid/
---

Syntax
------

-   [getpartnerid](/getpartnerid "wikilink")()

Description
-----------

This function returns the [character ID](/CID "wikilink") of the invoking character's [marriage](/marriage "wikilink") partner, if any. If the invoking character is not married, it will return 0, which is a quick way to see if they are married:

Examples
--------

`prontera,164,153,3 script  Manfred 60,{`
`   `[`mes`](/mes "wikilink")` "[Manfred]";`
`   `[`if`](/if "wikilink")` (`**`getpartnerid`**`()){ `
`       mes "You're married!";`
`   } `[`else`](/else "wikilink")` {`
`       mes "Awww, you're not married.";`
`   }`
`   `[`close`](/close "wikilink")`;`
`}`

Another example to retrieve character name of partner using **getpartnerid**()

`mapname,x,y,z  script  Charname    60,{`
`if (`[`getpartnerid`](/getpartnerid "wikilink")`()){`
[`query_sql`](/query_sql "wikilink")``  "SELECT `name` FROM `char` WHERE `char_id`="+ ``[`getpartnerid`](/getpartnerid "wikilink")`()+" ",@name$;`
` mes "Your Partner name is "+@name$;`
`} else {`
`mes "You don't have any partner";`
`}`
`close;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")