---
title: Texture
permalink: /Texture/
---

Texture Editing
---------------

There are 2 types of Texture editing. The first is editing the ground textures of maps the second is the textures of objects or models used in maps.

Map Texture Editing
-------------------

Map textures are easy to make, load Photoshop, paint .net or even just paint and create a square image (Normal map images are either 256x256 or 512x512 pixels) then draw your image and save it as a 256 color bmp (You can make them higher but 256 color images take less space, have less issues and you don't need all the extra colors) to what ever locaion you desire in your client's data folder (You can make your own folder when it's your textures for your maps).

Adding A Texture To A Map
-------------------------

If you are using Browedit you'll need to edit the texture text file within Browedit's data folder (It can be handy to make your own but if you do you will have to add it to the config file your using). The texture files are structured in a simple way, which is, menu location and display name followed by directory location then file name (Eg. sets/prontera/forest/grass_path-curve1|ÇÊµå¹Ù´Ú\\pron-dun-03.bmp). You can even set out how you want the menu listing for added sections by simply having just the menu location listed without any display names or file or folder listings (Eg. floor/carpet/|). This way you can structure your texture file at the beginning and list the textures afterwords. If you have successfully added your next map texture or textures to one of Browedit's texture files you'll be then able to find your texture in the texture window under what you put it under. If you are having trouble with the texture file just follow how one of the files is listed in there already.

Model Texture Editing
---------------------

If you are like some and wish to edit the textures of an object (aka model) and may or may not wish to replace the existing model then read on. Also like map textures, model textures are simple bmp files which any image editor should be able to open and edit. But while this is so, transparency on models seems to be lost when replaced by another (Borf may fix this in Browedit).

-   Remember to make sure your textures are 256 color bmp files when you save them or they may not work.

Replacing a Model's Texture
---------------------------

With Browedit replacing a model's texture is as easy as pie. Load browedit and under 'Windows &gt; RSM Editor' open the model you wish to edit then click the texture you wish to replace and in the texture window (Just like map textures you will have to have added your model texture or textures if you wish to replace any textures) and once you have clicked on the new texture the old will be replace by the new and you can save your creation. It's that simple.

-   Note. If you do not want to replace a model's texture but instead make a copy and replace it then just remember to click 'save as' (as save will replace the opened model) and rename the model file and then just like the map textures add it to the model list file in Browedit's data folder

[Category:Mapping](/Category:Mapping "wikilink")