---
title: Function
permalink: /Function/
---

Syntax
------

-   function<tab>script<tab><function name><tab>{<code>}

Description
-----------

This will define a function object, callable with the '[callfunc](/callfunc "wikilink")' command (see below). This object will load on every map server separately, so you can get at it from anywhere. It's not possible to call the code in this object by anything other than the '[callfunc](/callfunc "wikilink")' script command.

The code part is the script code that will execute whenever the function is called with '[callfunc](/callfunc "wikilink")'. It has to be in curly brackets, unlike elsewhere where we use curly brackets, these do NOT signify an optional parameter.

Usage
-----

`function   script  Test-Function   {`
`if(.@x == 1)`
`    set .@y,1;`
`else`
`    set .@y,0;`
`return;`
`}`