---
title: Gettimetick
permalink: /Gettimetick/
---

Syntax
------

-   **gettimetick**(<type>);

Description
-----------

This function retrieves various ticks, depending on provided *type*:

-   0: Returns server's tick, which is a measurement in milliseconds used by the server's timer system, typically amount of milliseconds since last boot. The server's tick is an unsigned int which loops every ~47 days.
-   1: Second of Day (0: 00:00:00 - 86399: 23:59:59)
-   2: Seconds since January 1, 1970 00:00:00 UTC (UNIX epoch)

Any other value defaults to 0. This function is especially useful for measuring of short time spans. For cases where time requires to be stored and remain valid across restarts, [gettime](/gettime "wikilink") should be considered instead.

Examples
--------

[`mes`](/mes "wikilink")` "I already wasted "+gettimetick(1);`
`mes "seconds of this day,";`
`mes "what a misfortune...";`

[Category:Script Command](/Category:Script_Command "wikilink")