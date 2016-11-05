---
title: Sprite Recolors
permalink: /Sprite_Recolors/
---

Recolors
--------

Sprite Recolors are sprites with a new [palette](/Palettes "wikilink") added (that also means that recolors use the same [act](/Acts "wikilink") the original sprite uses). You must have a palette file based on the sprite you want to recolor, if not, the recolored sprite will probably look weird. So, the best you can do for recoloring is taking a bmp or more from the original sprite and check their color tables.

When the color table window pops up, change the colors you feel like and then save the changes as "Microsoft Palette file".

Applying the palette
--------------------

Once you have your new palette, open the original sprite with SPR Conview and click on "Palette &gt; Open a Palette" (Open your palette then). Animate the sprite to see how the new colors look in all the frames. If you like them, save the file ("File &gt; Save"). If not, open another palette or click on "Palette &gt; Restore Palette" to get the original palette applied to the sprite again.

Keep in mind that every image needs to have a palette complementary to its current palette. If you have an image with 50 colors with a gradient of 16 tiles and then you add the [RO common colors](/RO_Pixeling_Colors "wikilink") palette, colors will look messed up. And if you have an image with 256 colors in its color table and add a palette with only 8 colors, it will look even worse (probably with neon colors messed up).

Changing the saturation and brightness
--------------------------------------

You can edit the brightness and saturation of your frames, changing automatically the original color table. You just have to change the brightness and saturation of one frame and then, open the color table. You will see that all colors have changed. Save the palette and then apply it to the sprite.

This way, you haven't touched the color table, but the saturation/brightness of your frame and then saved the palette. This is the best way to change saturation and brightness, because if you try to do it in the color table, you will spend a lot of time.

See also
--------

-   [Spriting](/Spriting "wikilink")
-   [Palettes](/Palettes "wikilink")

[Category:Spriting](/Category:Spriting "wikilink")