---
title: Day
permalink: /Day/
---

Syntax
------

-   **day**;
-   **night**;

Description
-----------

These two commands will switch the entire server between day and night mode respectively. If your server is set to cycle between day and night by [configuration](/:Category:Configuration "wikilink"), it will eventually return to that cycle.

Examples
--------

`-  script  DayNight    -1,{`
`   `[`end`](/end "wikilink")`;`
[`OnClock`](/OnClock "wikilink")`0600:`
`   day;`
`   end;`
[`OnInit`](/OnInit "wikilink")`:`
`   // setting correct mode upon server start-up`
`   `[`if`](/if "wikilink")`(`[`gettime`](/gettime "wikilink")`(3)>=6 && gettime(3)<18)`
`   {`
`       end;`
`   }`
`OnClock1800:`
`   night;`
`   end;`
`}`

This script allows to emulate the day/night cycle as the server does, but also allows triggering additional effects upon change, like announces, gifts, etc. The day/night cycle set by configuration should be disabled, when this script is used.

See Also
--------

-   [isday](/isday "wikilink")
-   [isnight](/isnight "wikilink")

[Category:Script Command](/Category:Script_Command "wikilink")