---
title: Weather without using mapflag
permalink: /Weather_without_using_mapflag/
---

[Category:Data](/Category:Data "wikilink") [Category:Client Configuration](/Category:Client_Configuration "wikilink")

Procedures
----------

First, create a file in your **/data/** folder or the root of your GRF then name the file **etcinfo.txt**.

After that, place the following codes inside the file: <code>

    weather#
    comodo.rsw#
    pokjuk#
    weather#
    brasilis.rsw#
    sakura#
    weather#
    prontera.rsw#
    snow#
    //File end

</code>

You can add the effect right before the last pound (\#) sign.

-   **pokjuk** = Fireworks
-   **sakura** = Sakura
-   **snow** = Snow

That's it. This is another way of adding weather to a particular map.

Other way of adding weather
---------------------------

You can as well add a script with [OnInit](/OnInit "wikilink") label to call it off. Here's a sample script:

`prontera,143,185,1    script    Sakura    -1,{ `
`// We will do a script instead of function for it to call on the exact map and the exact coordinates. But you can use as well `**`function`**` then instead of `**`script`**`.`
`// We will also use -1 since we don't want to display the actual NPC. In other words, -1 will make the NPC invisible.`
`end;`
`OnInit:`
`    atcommand "@sakura"; // You can change `**`@sakura`**` to @snow, @clouds, @clouds2, @fog, @fireworks or @leaves`
`    end;`
`}`