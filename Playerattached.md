---
title: Playerattached
permalink: /Playerattached/
---

Syntax
------

-   **playerattached**();

Description
-----------

Returns the [RID](/RID "wikilink") of the player currently attached to the script. It will return 0 if none is attached, or if the attached player is no longer on the map server. It is wise to check for the attached player in script functions that deal with timers as there is no guarantee the player will still be logged on when the timer triggers.

Example
-------

[`mes`](/mes "wikilink")` "Please wait for a bit...";`
[`sleep2`](/sleep2 "wikilink")` 5000;`
[`if`](/if "wikilink")`(!playerattached())`
`{`
`    `[`announce`](/announce "wikilink")` "It appears, that the winner could not even wait 5 seconds for the prize..",bc_all;`
`    `[`end`](/end "wikilink")`;`
`}`
[`getitem`](/getitem "wikilink")` 512,100;  // Apple`
`mes "Here you go, enjoy your prize.";`
[`close`](/close "wikilink")`;`

[Category:Script_Command](/Category:Script_Command "wikilink")