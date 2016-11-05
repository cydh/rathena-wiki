---
title: Select
permalink: /Select/
---

Syntax
------

-   **select**("<option>"{,"<option>",...});
-   **select**("<op tion>{:<option>:<option>}");
-   **[prompt](/prompt "wikilink")**("<option>"{,"<option>",...});
-   **[prompt](/prompt "wikilink")**("<option>{:<option>:<option>}");

Description
-----------

This function is a handy replacement for '[menu](/menu "wikilink")' for some specific cases where you don't want a complex label structure - like, for example, asking simple yes-no questions. It will return the number of menu option picked, starting with 1. Like '[menu](/menu "wikilink")', it will also set the variable @menu to contain the option the user picked.

And like '[menu](/menu "wikilink")', the selected option is consistent with grouped options and empty options.

'[prompt](/prompt "wikilink")' works almost the same as '[select](/select "wikilink")', except that when a character clicks the Cancel button, this function will return 255 instead.

Examples
--------

[`if`](/if "wikilink")`(`[`select`](/select "wikilink")`("Yes:No") == 1) `[`mes`](/mes "wikilink")` "You said yes, I know.";`
[`select`](/select "wikilink")`("21","22","23");`
[`set`](/set "wikilink")` .@opt,20+@menu;`
[`set`](/set "wikilink")` .@choice$,"Apple:Banana:Lemon";`
[`select`](/select "wikilink")`(.@choice$);`
[`explode`](/explode "wikilink")`(.@option$,.@choice$,":");`
[`mes`](/mes "wikilink")` "You have chosen "+.@option$[@menu-1];`

[Category:Script_Command](/Category:Script_Command "wikilink")