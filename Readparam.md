---
title: Readparam
permalink: /Readparam/
---

Syntax
------

-   **readparam**(<parameter number>{,"<character name>"});

Description
-----------

This function will return the basic stats referred by the parameter number of an invoking character or, if a character name is specified, of that player. Instead of a number, you can use a parameter name if it is defined in .

For reference, in there these things are defined:

`StatusPoint, BaseLevel, SkillPoint, Class, Upper, Zeny, Sex, Weight, MaxWeight, JobLevel, `
`BaseExp, JobExp, NextBaseExp, NextJobExp, Hp, MaxHp, Sp, MaxSp, BaseJob, Karma, Manner, `
`bVit, bDex, bAgi, bStr, bInt, bLuk`

All of these also behave as variables, but don't expect to be able to just '[set](/set "wikilink")' all of them - some will not work for various internal reasons.

Other Information
-----------------

This will return the status points you haven't spent yet:

-   readparam(9)

Using this particular information as a function call is not required. Just putting **StatusPoint** will give you the same result, and some of these parameters work just like variables (i.e. you can 'set Zeny,100' to make the character have 100 Zeny, destroying whatever Zeny they had before, or 'set Zeny,Zeny+100' to give them 100 Zeny)

Examples
--------

`  readparam(bVit)`
`      `[`if`](/if "wikilink")` (readparam(bVit)<=77) goto L_End;`
`      `[`mes`](/mes "wikilink")` "Only people with over 77 Vit are reading this";`
`  `
`  L_End:`
`      `[`close`](/close "wikilink")`;`

[Category:Script Command](/Category:Script_Command "wikilink")