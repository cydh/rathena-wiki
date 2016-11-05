---
title: Spriting
permalink: /Spriting/
---

Creating Your Own Frames
------------------------

You will need

-   Image Editing Software (e.g. [Photoshop](/wikipedia:Adobe_Photoshop "wikilink"))
-   Concept
-   Skill

When creating a new image, it is recommended that you use the bitmap format. The size itself depends on what it is you are planing to make. It does not need to be a particular size (only the inventory item sprite and .bmp image must have a size of 24x24 px, it is recommended that the drop sprite be this size too), but remember the bigger it is the more likely it is to look odd inside the game (and if your frames are too big, there is a big chance of getting an error ingame). The background needs to 'Magenta'. The hexadecimal format of this color is \#FF00FF. The RGB for this color is R 255, G 0, B 255.

Now that you have the size and everything figured out, its time to change it from .bmp to indexed color. Download this file: [RO common colors](/RO_Pixeling_Colors "wikilink"), then navigate to Image &gt; Mode &gt; Indexed Color... In the window that pops up, the palette can be anything you want, but if forced you select Custom... Then select load and change file type from .act to .pal, then find the .pal file then select and open it, it will be wherever you saved the file to. Once it has loaded, make sure the colors are 256, then select OK, then you will now have an image compatible with ragnarok, and you can now draw out your image. After this you can save your image as .bmp (bitmap).

You must get familiarized with this color table (you can access to your color table in Photoshop through Image &gt; Mode &gt; Color Table). First color in the color table is the transparency color. This means that ingame, this color won't appear. This color must be \#FF00FF for inventory items (you can change the colors of the color table by clicking on them. You can also make color gradients by selecting a group of colors if you are working with Photoshop). It can be any other color for Mobs, Jobs, Headgears, etc. However, It is recommended to use this color as background transparency color. Make sure background color is the first color in the color table. It is common that color \#FF00FF (magenta) appears as the third color in the color table, and not first. If you are working with inventory items images, you must change this color to any other color and make first color \#FF00FF. Then, you must change the background color to \#FF00FF manually (replacing the background color for \#FF00FF). We do this because you may have two magenta's in your color table (one in the first cell and another one in the third). If this happens and you make your background color \#FF00FF you may be using the third color, and not first. What will happen then? It will make a part of your inventory skin background disappear. So background color must be always the first color in the color table, and when we are working with inventory items, it also must be color \#FF00FF.

Some spriters usually use some neon colors as references, to make the edges of their sprite before coloring it. It is recommended you start making only the edges, so you can concentrate only in the perspective and size of your sprite without caring about shading. Neon colors are pretty visible, so if you happen to need them, add some neon colors to your color table and then use them in your frame.

Finally, when you finished making your base image for pixeling, you can put an image of the color table and pick colors with the eyedropper. If you are working with paint, in example, you can cut and paste an image with all the RO common colors. There is a small [table of RO colors](http://www.divinero.net/devilevil/PixelingColorsTable.bmp) that you can use for this.

Making A Sprite
---------------

As soon as you have one frame (8bits/256 colors bmp image), you will be able to create your sprite. For this, you will need a SPR maker. You can use [SPR Conviewer](http://www.divinero.net/devilevil/archivos/tools/SPRConviewer.rar) (made by bakausagi) to make your sprite. Once you opened SPR conview, you will have to go to "Convert &gt; Bmp to SPR" (only works with 8 bits bmp images). Click on "Add" and select all your frames. Try to name them like "Frame1", "Frame2", etc. and then select them all at the same time. If not, the order of frames in the sprite may not be correct. Avoid using control + click to add more frames. Select them all and if you selected something you don't want, just use control + click to deselect it. But don't use it to select frames because it may mess the frames up. Then, browse the directory where you want to save the sprite. When you finished with that, disable "encode" (because the frames may appear messed up and cut). Click convert and then open the sprite in conview to make sure it looks right.

There are other sprites that don't use 8 bits bmp images, but 32 bits TGA images. Those can only be made with [Actor](http://ratemyserver.net/index.php?page=download_tool) (either 1 or 2). You must add image per image and then save it as a sprite. You can't open these sprites with SPR Conview. The making of this sprite is different and more advanced, but you will be able to use four channels (RGB and Alpha).

Editing a Sprite
----------------

Remember that if this is a custom sprite that someone else made, to first ask permission before editing the sprite. Use a tool like SPR Conview to first convert the sprite from .spr (sprite) format to .bmp (bitmap) format. To be safe your sprite should have the same frame's as the one you are editing (if you plan to make a whole new sprite based off the original), but it is not required. If you are to share your sprite with the community, please include the words "Originally made by: (Username here)", as the original owner may get angry.

Simple Way To Prevent Theft
---------------------------

**Note: This doesn't guarantee that your sprite is safe. But if this frame is included you have definitive proof that the sprite is yours.**

Simply include a frame with the sprite that has your username or name on it, it may show up in game depending on what kind of sprite it is. Just make sure you have all the frames required filled, then include one extra frame with your credits. For example the drop sprite for an item only needs one frame, so you can include a second with your credits. The maximum size the credit frame can be is 179x33.

If you had different versions of the sprite you can also include one frame or a screen shot of the frames as evidence.

You can also put your username on the collection image. This can be easily removed from the folder, but most servers do not remove the collection image.

See also
--------

-   [Data](/:Category:Data "wikilink")
-   [Database](/:Category:Database "wikilink")
-   [Palettes](/Palettes "wikilink")
-   [Sprite Recolors](/Sprite_Recolors "wikilink")
-   [Pixeling](/Pixeling "wikilink")

[Category:Spriting](/Category:Spriting "wikilink")