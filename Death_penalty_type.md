---
title: Death penalty type
permalink: /Death_penalty_type/
---

Death penalty refers to a penalty that should be applied to a player who has died. This death penalty can be applied to players who die in a specific map or if they die anywhere (this applies for the EXP loss). Some of these penalties can be **EXP**, **Zeny**, and even **Item** loss. You can find configuration for **EXP** and **Zeny** loss through .../conf/battles/[exp.conf](https://raw.githubusercontent.com/rathena/rathena/master/conf/battle/exp.conf) while **Items** can be configured through .../npc/mapflag/[nightmare.txt](https://raw.githubusercontent.com/rathena/rathena/master/npc/mapflag/nightmare.txt)

Losses
------

Some losses stated in the .../conf/battles/[exp.conf](https://raw.githubusercontent.com/rathena/rathena/master/conf/battle/exp.conf) are:

`// When a player dies, how should we penalize them?`
`// 0 = No penalty.`
`// 1 = Lose % of current level when killed.`
`// 2 = Lose % of total experience when killed.`
`death_penalty_type: 1`
`// Base exp. penalty rate (Each 100 is 1% of their exp)`
`death_penalty_base: 100`
`// Job exp. penalty rate (Each 100 is 1% of their exp)`
`death_penalty_job: 100`
`// When a player dies (to another player), how much zeny should we penalize them with?`
`// NOTE: It is a percentage of their zeny, so 100 = 1%`
`zeny_penalty: 0`

**Note:** *Zeny loss is based within maps with the [PvP Mapflag](/Mapflag#pvp "wikilink").*

Nightmare Mode
--------------

Moving out from .../conf/battles/[exp.conf](https://raw.githubusercontent.com/rathena/rathena/master/conf/battle/exp.conf), head into .../conf/mapflag/[nightmare.txt](https://raw.githubusercontent.com/rathena/rathena/master/npc/mapflag/nightmare.txt). In this mapflag, you get to specify what items players can drop on their death within whatever map you wish (It's not just for PvP Maps since you can also die by monsters.. not just players).

The structure for this is as followed:

<map><tab>`mapflag`<tab>`pvp_nightmaredrop`<tab><ID>`,`<type>`,`<percent>

-   **ID** stands for an <ITEMID> or could be set by using the word "random" which will indicate any random equipment.
-   **Type** indicates either **Inventory**, **Equip**, or **All**. **Inventory** means that items will only be dropped if it is in that player's inventory while **Equip** means items that are currently equipped by the player and **All** will drop any item within their inventory (and equipped).
-   **Percent** is obviously the percent in which you want the item to be dropped.
    -   Example:



30 = .3%

300 = 3%

3000 = 30%

10000 = 100%

See Also..
----------

-   [Mapflag](/Mapflag "wikilink")
