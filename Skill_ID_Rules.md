---
title: Skill ID Rules
permalink: /Skill_ID_Rules/
---

### Skill Ranges

-   Homunculus Skills
    -   *Slots available:* 44 skills (**mmo.h::MAX_HOMUNSKILL**)
    -   *From:* 8001 (**mmo.h::HM_SKILLBASE**)
    -   *To:* 8044 (max. to 8200)
-   Mercenary Skills
    -   *Slots available:* 40 skills (**mmo.h::MAX_MERCSKILL**)
    -   *From:* 8201 (**mmo.h::MC_SKILLBASE**)
    -   *To:* 8240 (max. to 8400)
-   Elemental Skills
    -   *Slots available:* 42 skills (**mmo.h::MAX_ELEMENTALSKILL**)
    -   *From:* 8401 (**mmo.h::EL_SKILLBASE**)
    -   *To:* 8442 (max. to 9999)
-   Guild Skills
    -   *Slots available:* 16 skills (**mmo.h::MAX_GUILDSKILL**)
    -   *From:* 10000 (**mmo.h::GD_SKILLBASE**)
    -   *To:* 10015 (max. to 10999)
-   Player Skills
    -   *Slots available:* 5020 skills (**mmo.h::MAX_SKILL**)
    -   *From:* 0
    -   *To:* 5019 (max. to 5019)

### Do NOT Use These!

Before making skill for player, please be aware of these:

-   **Don't use 0!** because in many cases, 0 is identified as *invalid skill*
-   **Reserved ID**, don't use one of ID in these ranges, because these IDs are as Skill Indexes (value maybe changed if the [Skill Ranges](/Skill_ID_Rules#Skill_Ranges "wikilink") are changed )
    -   **700 ~ 743**, Homunculus Skill Indexes
    -   **744 ~ 784**, Mercenary Skill Indexes
    -   **785 ~ 827**, Elemental Skill Indexes
    -   **828 ~ 943**, Guild Skill Indexes
-   mmo.h::MAX_SKILL is 5020, if using ID more than 5019, ID will be invalid for **player's skill**, or can use the values more than 5019 but need to add the \#define MAX_SKILL value.


*(the current MAX_SKILL is kind of waste space! Even in Renewal, skill is less than 2000)*

### Empty Values

Some IDs maybe has been used by official skills, but these spaces can be used:

-   **1020 ~ 2000**
-   **2100 ~ 2200**
-   **2600 ~ 3000**
-   **3100 ~ 5000**

*Those ranges are rounded up. You can see the detail in or *