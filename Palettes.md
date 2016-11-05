---
title: Palettes
permalink: /Palettes/
---

What you need
-------------

-   SPR Conview
-   Photoshop or something else that can make .pal palette files

Editing Pallets With Photoshop
------------------------------

Editing pallets with Photoshop is a simple task. Simply load a sprite with a sprite viewer such as SPR Conview or SprTool+4-6 and export a single frame of the sprite as an image and load it with Photoshop. If your doing job sprites use a image from the job class you wish to make your pallet for and the same goes for hairs, head gear and monsters. As each sprite can have it's own pallet.

[Image:SPR Conview.jpg](/Image:SPR_Conview.jpg "wikilink") [Image:sprite.jpg](/Image:sprite.jpg "wikilink")

Once loaded into Photoshop load the color table via the 'Image &gt; Mode &gt; Color Table' like so:

[Image:load color table.jpg](/Image:load_color_table.jpg "wikilink")

If the color table is grayed out then the image isn't 256 colors and you won't be able to proceed. Once the color table window is up you'll see the range of colors available and used in the original sprite. Edit them is simple, either click a single color box or select a group (Selecting a group allows you to easily create a gradient range of colors by picking a light color and then picking a darker color, remember to click the 'ok' button.) then pick the new color or enter in the color values into any of the color boxes.

[Image:edit color table.jpg](/Image:edit_color_table.jpg "wikilink")

Once your new pallet is created simple click the save button in the color table window and save your pallet to a .pal file.

Editing The .Pal File For Use in Ragnarok With Notepad
------------------------------------------------------

Ragnarok Online Pallet files are simply normal pallet files (.pal) with the header removed. Simply open the file like so

[Image:notepad1.jpg](/Image:notepad1.jpg "wikilink")

Then selecting whats highlighted in the image and delete it and save. It's that simple.

Editing The .Pal File For Use in Ragnarok Without Notepad
---------------------------------------------------------

If you have a tool or something please fill in this area.

Replacing A Sprite's Pallet
---------------------------

Replacing a sprite's pallet in order to recolor it there are a few options, the most simple and probably the easiest way is to load the sprite into SPR Conview and under 'Pallet &gt; Open Pallet' select the pallet you made before (normal non RO pallet) and then save the sprite. It's that easy.

Client naming scheme for palettes
---------------------------------

Cloth palettes go to **data\\palette\\¸ö\\** (data\\palette\\몸\\), each file name follows the pattern **<jobname>_<gender>_<palette id>.pal**, ex. ¸¶¹ý»ç_¿©_4.pal (마법사_여_4.pal) for a female wizard palette).

The hair palettes go to **data\\palette\\¸Ó¸®\\** (data\\palette\\머리\\) and follow the pattern '''¸Ó¸®

<head sprite id>
_<gender>_<palette id>.pal''', ex. ¸Ó¸®8_¿©_2.pal (머리8_여_2.pal) for a female head sprite 8.

Technical Support, or FAQs
--------------------------

-   Q: My palettes won't show up in game, it says invalid number, I cannot access my palettes in the dye changer. How do I fix this?
-   A: Athena servers must have the conf settings changed to support new palettes for dyes before commands and npcs can use them. Once the conf is edited the dye npc your using must also have it's max dyes increased in number or players will not be able to select any new dyes. Also not all jobs have their own pallet files. Most jobs will use the pallets of the first jobs that come before them instead of using their own, this was done in order to save space in the grf file and thou save on download bandwidth, also time and effort in making them.
-   Q: My palette shows up as black with a bunch of neon lines and crap. Why?
-   A: This could be a variety of things. The main reason is usually because they are not places in the right spot, and your client just doesn't error for palettes. This is due to the client not finding any pallet files because their either in the wrong place or incorrectly named. Job pallets and hair pallets have their own folders along with a folder for each sex and then the file name is made up of the job name (or hair) sex and then the number pallet. Another reason could be that you didn't convert it to RO format by removing the things pictured above. Make sure you do that.

[Category:Spriting](/Category:Spriting "wikilink")