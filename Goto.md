---
title: Goto
permalink: /Goto/
---

Syntax
------

-   [goto](/goto "wikilink") <label>;

Description
-----------

This command will make the script execution jump to the specified label. It is often used by beginners in conjunction with [if](/if "wikilink"), before they get accustomed to other conditional statements, such as [for](/for "wikilink") or [switch](/switch "wikilink"). While advanced scripters typically discourage using [goto](/goto "wikilink"), it can come handy when requiring to leave a complex nested loop without having to use flags or even more complicated code.

Examples
--------

[`if`](/if "wikilink")` (`[`checkriding`](/checkriding "wikilink")`()) `[`goto`](/goto "wikilink")` L_riding;`
`   `[`mes`](/mes "wikilink")` "Yay, you're not riding a Peco.";`
`   `[`close`](/close "wikilink")`;`
`L_riding:`
`   `[`mes`](/mes "wikilink")` "Please dismount your Peco first.";`
`   `[`close`](/close "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink")