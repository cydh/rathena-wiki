---
title: Isloggedin
permalink: /Isloggedin/
---

Syntax
------

-   **isloggedin**(<account id>\[, <char id>\]);

Description
-----------

This function checks, whether an character with given [account id](/AID "wikilink") is currently online (1) or not (0). Additionally a [char id](/CID "wikilink") can be specified, for exact character matching.

Examples
--------

[`input`](/input "wikilink")` .@aid;`
`if(isloggedin(.@aid))`
`{`
`    `[`mes`](/mes "wikilink")` "A character with account id "+.@aid+" is currently around.";`
`}`
`else`
`{`
`    mes "Sorry, there is no character online with account id "+.@aid+",";`
`    mes "or the account does not exist.";`
`}`

See Also
--------

-   [attachrid](/attachrid "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")