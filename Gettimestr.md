---
title: Gettimestr
permalink: /Gettimestr/
---

Syntax
------

-   **gettimestr**(&lt;"format"&gt;, <max length>);

Description
-----------

This function returns the current system time and date as a string, according to given *format*, which has same syntax as the one of C library function [strftime](http://www.cplusplus.com/reference/clibrary/ctime/strftime/). The parameter *max length* specifies the maximum length of the string returned.

Examples
--------

[`mes`](/mes "wikilink")` gettimestr("%Y-%m/%d %H:%M:%S",21);`

Would print out the full current date and time, ex. "2010-10/30 07:48:37".

[More Example](http://pastebin.com/raw.php?i=REsVJLmE)

[Category:Script Command](/Category:Script_Command "wikilink")