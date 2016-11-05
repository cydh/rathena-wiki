---
title: BuildBot
permalink: /BuildBot/
---

[BuildBot](/BuildBot "wikilink") is a software development [continuous integration](/wikipedia:Continuous_integration "wikilink") tool which automates the [compile](/wikipedia:compiler "wikilink")/test cycle required to validate changes to the project code base. BuildBot is written in [Python](/wikipedia:Python_(programming_language) "wikilink") on top of the [Twisted](/wikipedia:Twisted_(software) "wikilink") libraries.

rAthena BuildBot
----------------

Developers *should* test their changes before committing. To help double-check each commit and also test compatibility on other operating systems, we have setup a [BuildBot](/wikipedia:BuildBot "wikilink").

<http://build.rathena.org/>

### BuildBot features

-   polls the SVN every 60 seconds for new changes to /
-   after a new commit, waits 2 minutes before triggering a build (if there is another commit within 2 minutes, the timer is reset)
-   compiles the servers, and checks for compile warnings/errors
-   starts map-server_sql, and checks for script/db warnings/errors

### [BuildBot status page](http://build.rathena.org/)

-   The **[Waterfall Display](http://build.rathena.org/waterfall)** will give you a time-oriented summary of recent buildbot activity. [Waterfall Help.](http://build.rathena.org/waterfall/help)
-   The [Grid Display](http://build.rathena.org/grid) will give you a developer-oriented summary of recent buildbot activity.
-   The [Transposed Grid Display](http://build.rathena.org/tgrid) presents the same information as the grid, but lists the revisions down the side.
-   The **[Console](http://build.rathena.org/console)** presents a user-oriented status page.
-   The [Builders](http://build.rathena.org/builders) and their most recent builds are here.
-   The [Latest Build](http://build.rathena.org/one_box_per_builder) for each builder is here.
-   [Recent Builds](http://build.rathena.org/one_line_per_build) are summarized here, one per line.
-   [Buildslave](http://build.rathena.org/buildslaves) information
-   [ChangeSource](http://build.rathena.org/changes) information

BuildSlaves
-----------

One or more buildslaves are connected to the buildmaster in a star topology. Buildslaves are typically run on a variety of separate machines, at least one per platform of interest.

### Linux

-   [CentOS](/wikipedia:CentOS "wikilink") 6.3 (64-bit)
-   [Debian](/wikipedia:Debian "wikilink") Squeeze 6.0
-   [Ubuntu](/wikipedia:Ubuntu_(operating_system) "wikilink") 10.04
-   [Ubuntu](/wikipedia:Ubuntu_(operating_system) "wikilink") 12.04 (64-bit)

### Windows

-   [Windows 7](/wikipedia:Windows_7 "wikilink")

See Also
--------

-   [BuildBot home page](http://trac.buildbot.net/)
-   [How to contribute a buildslave to the rAthena BuildBot](http://rathena.org/board/topic/56220-buildbot-info-and-how-to-help/)

[Category:Debugging](/Category:Debugging "wikilink") [Category:rAthena](/Category:rAthena "wikilink")