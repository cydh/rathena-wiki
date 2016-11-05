---
title: EAthena
permalink: /EAthena/
---

eAthena
=======

**eAthena**, short for English Athena, is a cross-platform, open-source game server software for the popular MMORPG [Ragnarok Online](https://en.wikipedia.org/wiki/Ragnarok_Online). It is an emulation of the [Aegis](https://en.wikipedia.org/wiki/AEGIS_(Ragnarok_Online)) software created by Gravity Co., Ltd. that powers the official Ragnarok Online servers, and is used to run private servers. This is accomplished through modifying the game client provided by Gravity to connect to private, instead of official servers.

History
=======

Athena (commonly called jAthena, short for Japanese Athena, by non-Japanese speakers) was a Ragnarok Online game server emulation project that was started in late 2002. It was created because around this time, the official free-to-play Ragnarok Online servers exited the open-beta phase and became pay-to-play, and many players either did not want to or could not pay to play the game.

eAthena was initially born as AppleMod in late 2003, an English translation of Athena by a developer that went by the handle AppleGirl. AppleMod eventually forked from Athena and was renamed to eAthena in early 2004.

Specifications
==============

eAthena is coded in the C programming language and makes use of the zlib and MySQL libraries. The actual application is split into three servers - login, char, and map, each of which serve a different purpose. Support for multiple map servers is also possible. Thus, while the individual eAthena servers are single-threaded, they do essentially have support for running on multiple processes, and even on multiple computers.

For storage of dynamic game data, eAthena can be compiled to use one of two different modes of database operation: TXT or SQL. TXT is short for plain-text whereas SQL is MySQL. SQL is the standard way of running the eAthena servers. TXT is generally used merely only for testing and development purposes as a quick and convenient way to get eAthena up and running without having to deal with any 3rd-party software, and is not recommended for live, production servers.

eAthena uses plain-text databases for configuration of static game data such as item, monster, and skill information, although some of these can optionally be configured to use MySQL instead. Additionally, eAthena features a fully custom, C-like scripting engine for configuration of NPCs, quests, warp portals, and monster spawns, among other interactive in-game systems.

There have been talks of and attempts at improving the eAthena code base for years, including full-scale conversion to C++ (called eAPP), replacement of the TXT system with SQLite, and replacement of the script engine with Lua, but none of these ideas have ever been completed.

Comparison with Aegis
=====================

eAthena has proven to be a solid and very close emulation of Gravity's own Aegis software. This has been accomplished by analysis of both Gravity's Ragnarok Online client software and from Aegis itself, which has been leaked numerous times. Most of eAthena's databases and scripts have in fact been converted directly from leaked Aegis packages. eAthena's progress usually lags behind Aegis' an episode or so, as updated leaks are required to obtain new data.

eAthena is efficient, stable, and secure. Both Aegis and eAthena can handle thousands of players at once without issues, and security exploits that are discovered are quickly patched. However, eAthena (and by extension rAthena) interestingly has a number of notable advantages over Aegis, of which include the following:

-   It is cross-platform and can run on both Microsoft Windows and Unix-like platforms (such as Linux and Mac OS X), while Aegis is Windows-only.
-   It supports the free MySQL database software as well as plain-text databases while Aegis requires the proprietary Microsoft SQL Server software.
-   It is fully open-source thus allowing trivial custom modification, whereas only Aegis binaries and not source code have been leaked, making modifications limited and very difficult.
-   It is much easier to configure and setup than Aegis. Arguably, eAthena's databases and script engine are also easier to work with, more well-formatted, and better featured than those of Aegis.
-   It has many more features than Aegis and offers much greater customization. Examples include eAthena's far more robust in-game @command system versus Aegis' /command system and eAthena's powerful configuration system which allows alteration of many game functionalities without having to touch the source code, of which Aegis is nearly completely lacking, among others.
-   It requires far fewer resources than Aegis, namely in the area of memory. Aegis requires over 2 gb of RAM just to launch while eAthena can run on only several hundred megabytes, or even less than 100 mb using optional dynamic data allocation.
-   The number of 3rd-party software available for (e|r)Athena far exceeds those of Aegis.
-   On the other hand, on account of Aegis being a professionally developed software, it is likely to have greater stability and security than eAthena. Additionally, Aegis is Ragnarok Online exactly how it is and was intended to be, and while eAthena strives to be as close to accurate an emulation as possible, it is not perfect, and the game mechanics are slightly different in many areas.

As of 2010, there are approximately 500 private servers running eAthena, while there are around 30 official servers running Aegis. Despite Aegis being frequently leaked and available for use, it is rarely used to run private servers, primarily due to the various advantages of eAthena over it listed above.

Source(s)
=========

-   [eAthena Wikipedia](https://en.wikipedia.org/wiki/EAthena)
