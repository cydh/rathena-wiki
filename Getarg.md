---
title: Getarg
permalink: /Getarg/
---

Syntax
------

-   **getarg**(<index>\[,
    <default value>
    \]);

-   **getarg**(<index>\[, &lt;"default value"&gt;\]);

Description
-----------

This function retrieves a parameter inside a function, which was passed into an invoking [callsub](/callsub "wikilink") or [callfunc](/callfunc "wikilink") call. The parameters are referred to by an zero-based *index*, which means, the first parameter has index 0, the second parameter 1, and so on. Optionally a *default value* can be specified, which will be used, when no parameter was passed with given index (optional parameter functionality for script functions).

If there is no such parameter at given index and no default value exists, or if the invoking script is not a function, the script terminates with an error.

The parameter *default value* is available since .

Examples
--------

`    `[`callsub`](/callsub "wikilink")` L_dosomething, "toast";`
`    `[`end`](/end "wikilink")`;`
`L_dosomething:`
`    `[`mes`](/mes "wikilink")` "*does something with a "+getarg(0, "not recognized thing")+"*";`
`    `[`close2`](/close2 "wikilink")`;`
`    `[`return`](/return "wikilink")`;`

This results in message *\*does something with a toast\**. If "toast" were not passed as parameter, the message would be *\*does something with a not recognized thing\**.

[Category:Script Command](/Category:Script_Command "wikilink")