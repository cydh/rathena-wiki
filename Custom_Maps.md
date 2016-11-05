---
title: Custom Maps
permalink: /Custom_Maps/
---

Adding Custom Maps
==================

The process of adding in maps on the server end is relatively fool-proof, and is very easy to do. As long as you follow this guide, you should have few problems when attempting to add in the maps you want.

Conf Folder
-----------

### Maps_athena

First what you are going to want to do is open up 'maps_athena.conf' in the 'conf' folder, and scroll all the way to the bottom. Once you get there, just copy the format of how the other maps are listed, so it will be like map: Custom_Map. Remember not to use spaces, either use no spaces or underscores instead of spaces. Save that file and close it, we won't need it again. **NOTE:** Don't put .rsw at the end of the name, that is a depreciated method of placing maps(If it is even still supported).

### Grf-files

This is a short step, in the 'conf' folder again. Open up grf-files.txt and simply make sure that if your custom map is in a GRF, to add said GRF to the GRF list following the format provided in the file. If your map is in a data folder, make sure to add the correct path to your data folder in the data folder section, but do not include \\data in your path. Example:

`//-----------------------------------------`
`//GRF List`
`//-----------------------------------------`
`// grf: C:\path\to\RO\data.grf`
`// You may add more in this format`
`// grf: `<data file path>
`grf: C:\Program Files (x86)\Gravity\RO\data.grf`
`grf: C:\Program Files (x86)\Gravity\RO\rdata.grf`
`//------ Others ---------------------------`
`// Data Directory (without the actual data\ though)`
`// the below example would use C:\path\to\RO\data\`
`//data_dir: C:\path\to\RO\`
`data_dir: C:\Program Files (x86)\Gravity\RO\`

Db Folder
---------

The next modification needed is to a file called 'map_index.txt', which is located in the 'db' folder. As before, scroll to the bottom of the file. You may notice a header placed in // (Comment) tags, which tells you to place your custom map after it. Read it, and as before, follow the format this file is using for map entries, just type the name of your map then use the tab key and place 1250 for the starting id of your map.

Example: invek<tab>1250

Anyways, once you put an entry for your maps at the bottom of the file, save it and close it.

Before you leave the 'db' folder, you have the option of deleting the file 'map_cache.dat', which is what the server uses as a list of maps that it has installed. You can see the map_cache.dat inside your db/re folder the the renewal and db/pre-re folder for the pre-renewal. rAthena made a decision to have a two map_cache.dat because of renewal maps should not be appearing in your pre-renewal server.

If the server can't find a map on the list when something requests it, the server considers the map non-existant. I'm not sure of any issue existing that stems from deleting it (other than if you try to start the server without a new one generated), but if you feel uncomfortable in doing so, leave it alone. Regardless of whatever you chose to do, head up a folder, and look for the program 'mapcache.exe'. All you have to do is execute this program, and it will begin to either recreate the mapcache with your custom maps added, or simply skip along the already added maps and when it comes upon your custom maps, it will add them into the cache. **NOTE:** I like to open up a copy of cmd.exe that sits in the same folder and execute mapcache using it, which allows me to read the end output,(where you should see your custom maps being cached) just as a confirmation. **NOTE:** Whatever OS you use to create the mapcache, it should be valid on any OS rAthena is running on.

Fire up the server, and hop in-game to check if the map exists.

Client Side
-----------

Go into your data folder and locate 'mapnametable.txt'. Open it, scroll to the bottom, and as before follow the same format. Add your map's file name followed by .rsw and then in between the pound symbols, put what you want to show up as the name of the map when the user uses /where. Don't forget to add the .gat, .gnd and .rsw files of your new custom map to your data folder.

Example:

invek.rsw\#Town Of Beginnings\#

invek.rsw = your custom map file name (rsw).

Town Of Beginnings = The title of your custom map when a player uses /where command.

Common Errors
=============

### Successfully added, but in-game it doesn't exist

Run the mapcache again without deleting your mapcache you built the first time, and check the end output. If it states a second time that it 'Successfully Added' the map, and the server still states the map doesn't exists, this usually is a sign that the name of the map exceeds 11 characters (e.g.: hallowstation is 13 characters, while hal_station is 11), and can be confirmed if you check the map server's output for removed maps and find the first 11 characters of your maps name listed.

### Mapcache cannot find my map

Check to see if your settings in grf-files.txt are correct, and that the name of the map is correct in maps_athena.conf and map_index.txt

### /Where shows unknown map

That is due to a client side file not being updated, see above for more information.

### Black squares on my map that causes parts of it to flash

Black squares and flashing spots on the map are the result of saving the map in certain revisions. To ensure clear quality maps, it is recommended that users edit in BrowEdit r620 and save their maps in BrowEdit r586. If you're still experiencing black squares even after saving your maps in r586, it can be that your .rsw files are being saved with the wrong hex codes. To fix this, follow the instructions [here](https://rathena.org/board/topic/61531-resolved-browedit-help-about-walking/#entry92618). [Category:Customization](/Category:Customization "wikilink")