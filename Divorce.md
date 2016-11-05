---
title: Divorce
permalink: /Divorce/
---

Syntax
------

-   **divorce**();

Description
-----------

This function will "un-marry" the invoking character from whoever they were married to. Both will no longer be each other's marriage partner, (at least in latest GIT, which prevents the cases of multi-spouse problems). It will return 1 upon success or 0 if the character was not married at all.

This function will also destroy both wedding rings and send a message to both players, telling them they are now divorced.

Examples
--------

Here are two examples for divorce() usage:
This one is part of the custom rA marriage script:

`   `[`if`](/if "wikilink")` (!(`**`divorce`**`())) {`
`       `[`mes`](/mes "wikilink")` "["+@name$+"]";`
`       `[`mes`](/mes "wikilink")` "Where has "+$@divorcer$+" gone to? I can't divorce you unless you both are here...";`
`       `[`emotion`](/emotion "wikilink")` e_swt2;`
`       `[`close`](/close "wikilink")`;`
`   }`

This next example is a less efficient way to check, perform menu command, then execute divorce

[`mes`](/mes "wikilink")` "So you want to get a divorce?";`
[`menu`](/menu "wikilink")` " - Yeah!",L_Divorce," - Nah, i was only joking!",-;`
[`close`](/close "wikilink")`;`
`L_Divorce:`
`   `[`mes`](/mes "wikilink")` "Ok, let's get you un-married!";`
`   `[`next`](/next "wikilink")`;`
`   divorce();`
`   `[`mes`](/mes "wikilink")` "I've also destroyed your rings, just to make things official!";`
`   `[`close`](/close "wikilink")`;`

[Category:Script_Command](/Category:Script_Command "wikilink")