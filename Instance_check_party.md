---
title: Instance check party
permalink: /Instance_check_party/
---

Syntax
------

-   [instance_check_party](/instance_check_party "wikilink")(<party id>{,<amount>{,<min>{,<max>}}});

Description
-----------

This function checks if a party meets certain requirements, returning 1 if all conditions are met and 0 otherwise. It will only check online characters.

| Value  | Description                                                                  |
|--------|------------------------------------------------------------------------------|
| amount | number of online party members (default is 1).                               |
| min    | minimum level of all characters in the party (default is 1).                 |
| max    | maximum level of all characters in the party (default is max level in conf). |

Example
-------

`if (`[`instance_check_party`](/instance_check_party "wikilink")`(`[`getcharid`](/getcharid "wikilink")`(1),2,2,149)) {`
`   `[`mes`](/mes "wikilink")` "Your party meets the Memorial Dungeon requirements.",`
`   `[`mes`](/mes "wikilink")` "All online members are between levels 1-150 and at least two are online.";`
`   `[`close`](/close "wikilink")`;`
`} else {`
`   `[`mes`](/mes "wikilink")` "Sorry, your party does not meet requirements.";`
`   `[`close`](/close "wikilink")`;`
`}`

See Also
--------

-   [Instancing](/Instancing "wikilink")

[Category:Script_Command](/Category:Script_Command "wikilink")