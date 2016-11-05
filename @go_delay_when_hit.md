---
title: @go delay when hit
permalink: /@go_delay_when_hit/
---

**This source snippet is for putting a delay in @go when a player receives a damage.**
*open **src/map/pc.h***

:\* find:**unsigned int canuseitem_tick; // \[Skotlex\]**

:\* then add below:*' unsigned int warpgodelay_tick;*'
*open **src/map/pc.c***

:\* find: **sd-&gt;canuseitem_tick = tick;**

:\* then add below:**sd-&gt;warpgodelay_tick = tick;**
*open **src/map/pc.c***

:\* find: **void pc_damage(struct map_session_data \*sd,struct block_list \*src,unsigned int hp, unsigned int sp)**

:\* then add this inside the function:



unsigned int tick = gettick();

int warpgodelaycd = 5000; //This is the delay in milliseconds you can set what ever delay you want

sd-&gt;warpgodelay_tick = tick+warpgodelaycd; //This is the timer

*open **src/map/atcommand.c***

:\* find:**ACMD_FUNC(go)**

:\* then add this inside the function: **unsigned int tick = gettick();**
We are still in the @go function

:\* scroll down until you find this inside the function:**nullpo_retr(-1, sd);**

:\* then add below:



if(DIFF_TICK(sd-&gt;warpgodelay_tick,tick)&gt;0)

{



//This is for computing the delay if the cooldown or delay is not yet finish restrict using @go

clif_displaymessage(fd,"There is a 5 seconds delay in using @go command");

return 0;

}

[Category:Source Snippets](/Category:Source_Snippets "wikilink") [Category:Customization](/Category:Customization "wikilink")