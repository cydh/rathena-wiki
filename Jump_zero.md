---
title: Jump zero
permalink: /Jump_zero/
---

[Category:Script_Command](/Category:Script_Command "wikilink")

Syntax
------

-   [jump_zero](/jump_zero "wikilink")(<condition>),<label>;

Description
-----------

This command works kinda like an [if](/if "wikilink")+[goto](/goto "wikilink") combination in one go. If the condition is false (equal to zero) this command will immediately jump to the specified label like in [goto](/goto "wikilink"). While [if](/if "wikilink") is more generally useful, for some cases this could be an optimization.

The main reason for this command is that other control statements, like [switch](/switch "wikilink"), [for](/for "wikilink") or [while](/while "wikilink"), are disassembled into simple expressions together with this command when a script is parsed.