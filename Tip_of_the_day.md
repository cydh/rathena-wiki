---
title: Tip of the day
permalink: /Tip_of_the_day/
---

[thumb|280x180px|Typical tip of the day window](/Image:Tipoftheday.gif "wikilink") A window that contains various game related shortcuts, commands and usability tips for beginners. It appears on every game start, unless disabled, and after entering **/tip** in the chat window.

Customization
-------------

The available tips are stored inside the **tipOfTheDay.txt**, **tipOfTheDay_e.txt**, **tipOfTheDay_j.txt** or **tipOfDay.txt** file depending on the client type, in one-column [Token Text Table](/Token_Text_Table "wikilink") format. If the file is missing, the window appears empty. Translation packs contain the translated version of this file, if you do not want to create one on your own.

Registry
--------

The configuration for displaying the tip of the day on every start up is stored at

    HKEY_LOCAL_MACHINE\Software\Gravity Soft\Ragnarok

in value **SHOWTIPSATSTARTUP** (DWORD) where **0** means disabled and **1** means enabled.

[Category:Client_Configuration](/Category:Client_Configuration "wikilink")