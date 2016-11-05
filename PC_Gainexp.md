---
title: PC Gainexp
permalink: /PC_Gainexp/
---

Function to gain EXP
--------------------

`int pc_gainexp(struct map_session_data *sd, struct block_list *src, unsigned int base_exp,unsigned int job_exp)`
`pc_gainexp(sd, bl, X, Y);`

-   sd = ? (Looks like only players can gain exp?)
-   bl = ?
-   X = Base XP
-   Y = Job XP

Notes:

-   pc_nextbaseexp(sd) = XP necessary for next Base Level UP
-   pc_nextjobexp(sd) = XP necessary for next Job Level UP

`pc_gainexp(sd, bl, pc_nextbaseexp(sd), Y);`

This would be a FULL Base Lvlup, leaving with 0% on next level

`pc_gainexp(sd, bl, 0, pc_nextjobexp(sd));`

This would be a FULL Job Lvlup, leaving with 0% on next level

[Category:Source_Functions](/Category:Source_Functions "wikilink")