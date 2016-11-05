---
title: Folder Structure
permalink: /Folder_Structure/
---

| Location                     | Description                                                                                                                                               |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **/3rdparty/**               | 3rd party files, such as mysql.h                                                                                                                          |
| **/conf/**                   | Main configuration settings, such as connection settings, battle settings and [mapflags](/mapflag "wikilink").                                            |
| /conf/import/                | [Import folder](/Import_folder "wikilink"), mainly used to keep your configuration settings after an SVN update.                                          |
| /conf/battle/                | Where you will find settings to change the rates, drops, max stats and such for your server.                                                              |
| /conf/msg_conf/import/      | Used for importing message files.                                                                                                                         |
| /conf/msg_conf/import-tmpl/ | Template files for importing message files.                                                                                                               |
| /conf/msg_conf/             | Message files, available for English (default), Chinese, France, Germany, Indonesian, Portugese, Russian, Spain, and Thai                                 |
| **/db/**                     | Databases, such as the job_db, experience tables, item and mob flat-file databases.                                                                      |
| /db/import/                  | Database files for importing/customizations purpose.                                                                                                      |
| /db/import-tmpl/             | Template files for database import.                                                                                                                       |
| /db/pre-re/                  | Pre renewal database files.                                                                                                                               |
| /db/re/                      | Renewal database files.                                                                                                                                   |
| **/doc/**                    | Various documented settings, mainly for database settings.                                                                                                |
| /doc/samples/                | Sample scripts.                                                                                                                                           |
| **/log/**                    | If you generate any log files, such as **picklog** or **atcommandlog**, they will be stored and updated here.                                             |
| **/npc/**                    | Any NPC/spawn file you will find in the game is in here.                                                                                                  |
| /npc/airports/               | The airports and airship scripts are in here, and any NPC related to them.                                                                                |
| /npc/battlegrounds           | Battlegrounds scripts can be found in here.                                                                                                               |
| /npc/cities/                 | Any non-quest, non-kafra [NPC](/NPC "wikilink") found in the towns are here.                                                                              |
| /npc/custom/                 | Any NPC not officially supported by rAthena is located in here. Here is where you will find your healers, warpers and MVP arenas.                         |
| /npc/events/                 | Any official events, such as twin-towers or Christmas events on the official servers.                                                                     |
| /npc/guides/                 | Any guides in the cities.                                                                                                                                 |
| /npc/guild/                  | [WoE](/War_of_Emperium "wikilink") scripts and functions are in here.                                                                                     |
| /npc/guild2/                 | WoE:SE scripts and functions.                                                                                                                             |
| /npc/jobs/                   | Job changing scripts and quests, as well as functions.                                                                                                    |
| /npc/kafras/                 | Kafra scripts and functions.                                                                                                                              |
| /npc/mapflags/               | Folder with all the [mapflags](/mapflag "wikilink"), such as noteleport, pvp and gvg.                                                                     |
| /npc/merchants/              | Any official merchants in here.                                                                                                                           |
| /npc/mobs/                   | Spawn scripts for fields, dungeons as well as city cleaners in here.                                                                                      |
| /npc/other/                  | Scripts that don't really fit anywhere else, like the marriage script.                                                                                    |
| /npc/pre-re/                 | Pre Renewal scripts                                                                                                                                       |
| /npc/quests/                 | Official Quests, such as the Sign Quest or Thanatos Tower.                                                                                                |
| /npc/re/                     | Renewal scripts                                                                                                                                           |
| /npc/warps/                  | Warp portals, and scripts, that behave that way.                                                                                                          |
| **/save-tmpl/**              | If using TXT, this is where all your player information is to be stored, such as accounts, characters and guilds.                                         |
| **/sql-files/**              | If using SQL, this is where the pre-made database dumps are, that will populate your database with the correct tables and such.                           |
| **/src/**                    | All source files, the meat and potatoes of the emu.                                                                                                       |
| /src/char/                   | Character server source files.                                                                                                                            |
| /src/common/                 | Common between both TXT and SQL server settings. [mmo.h](/mmo.h "wikilink") is in here, the file that will modify most of the hard-coded server settings. |
| /src/config/                 | Some config source files, such as const.h, core.h, renewal.h, and secure.h                                                                                |
| /src/config/classes/         | Another config files, general.h.                                                                                                                          |
| /src/custom/                 | Alternative source files for 'simple' customization atcommand and script command.                                                                         |
| /src/login/                  | Login server source files.                                                                                                                                |
| /src/map/                    | Map server source files.                                                                                                                                  |
| /src/plugins/                | Plugins source files.                                                                                                                                     |
| /src/test/                   |                                                                                                                                                           |
| /src/tool/                   | [Tools](http://rathena.svn.sourceforge.net/svnroot/rathena/trunk/src/txt-converter/) source files, such as the mapcache maker.                            |
| **/tools/**                  | Contains tool scripts for various maintenance-related tasks.                                                                                              |
| **/vcproj-9/**               | Project 9 Files,Files used if Using MS Visual Studio C++ 2008                                                                                             |
| **/vcproj-10/**              | Project 10 Files,Files used if using MS Visual Studio C++ 2010                                                                                            |
| **/vcproj-12/**              | Project 12 Files,Files used if using MS Visual Studio C++ 2012                                                                                            |
| **/vcproj-13/**              | Project 13 Files,Files used if using MS Visual Studio C++ 2013                                                                                            |

