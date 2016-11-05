---
title: OnAgitInit
permalink: /OnAgitInit/
---

Special Lable
-------------

-   OnAgitInit:

Description
-----------

This special label will be ran as soon as the castle data is loaded from the char data. So it will check for the start and end time to see if it's in WoE time, hence why the hours has to be checked. There cannot be more than one of this line as it will cause confusion in your WoE script. On clock should always be typed before OnAgitInit.

Format
------

OnAgitInit should always appear right after OnClock labels and carry the time check list. The list should also be in order (Monday, Tuesday...).