---
title: Roclass
permalink: /Roclass/
---

Syntax
------

-   [roclass](/roclass "wikilink")(<job number> {,<gender>})

Description
-----------

Does the opposite of [eaclass](/eaclass "wikilink"). That is, given a eA Job class, it returns which is the corresponding RO class number. A gender is required because both Bard and Dancers share the same eA Job value (EAJ_BARDDANCER), if it isn't given, the gender of the executing player is taken (if there's no player running the script, male will be used by default). The command returns -1 when there isn't a valid class to represent the required job (for example, if you try to get the baby version of a Taekwon class).

A list of all id's is in :

Examples
--------

[`set`](/set "wikilink")` @eac, `[`eaclass`](/eaclass "wikilink")`();`
`// Check if class is already rebirth`
[`if`](/if "wikilink")` (@eac & EAJL_UPPER) {`
`   `[`mes`](/mes "wikilink")` "You look strong.";`
`   `[`close`](/close "wikilink")`;`
`}`
[`set`](/set "wikilink")` @eac, `[`roclass`](/roclass "wikilink")`(@eac | EAJL_UPPER);`
`// Check if class has a rebirth version`
[`if`](/if "wikilink")` (@eac != -1) {`
`   `[`mes`](/mes "wikilink")` "Bet you can't wait to become a "+`[`jobname`](/jobname "wikilink")`(@eac)+"!";`
`   `[`close`](/close "wikilink")`;`
`}`

[Category:Script Command](/Category:Script_Command "wikilink")