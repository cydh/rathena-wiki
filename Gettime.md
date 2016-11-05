---
title: Gettime
permalink: /Gettime/
---

Syntax
------

-   **gettime**(<type>);

Description
-----------

This function retrieves current system time and date values depending on parameter *type*:

1.  Seconds (0 - 59)
2.  Minutes (0 - 59)
3.  Hours (0 - 23)
4.  Day of Week (0: Sunday - 6: Saturday)
5.  Day of Month (1 - 31)
6.  Month (1 - 12)
7.  Year (1970 - 2038)
8.  Day of Year (1 - 366)

Any other value will cause the function to return -1. Only numbers are returned.

Examples
--------

[`if`](/if "wikilink")`(gettime(4)==6)`
`{`
`    `[`mes`](/mes "wikilink")` "It's a Saturday. I don't work on Saturdays.";`
`    `[`close`](/close "wikilink")`;`
`}`

See Also
--------

-   [gettimestr](/gettimestr "wikilink")
-   [gettimetick](/gettimetick "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")