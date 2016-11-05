---
title: PC Readglobalreg
permalink: /PC_Readglobalreg/
---

Check a variable in the source
------------------------------

`#define pc_readglobalreg(sd,reg) pc_readregistry(sd,reg,3)`

`pc_readglobalreg(sd,"VARIABLE_NAME");`

Note: This only works for numeric variables, strings check [pc_readglobalreg_str](/pc_readglobalreg_str "wikilink").

[Category:Source_Functions](/Category:Source_Functions "wikilink")