---
title: DATA.INI
permalink: /DATA.INI/
---

**DATA.INI** is a client-side file, which is used to specify multiple [GRF](/GRF "wikilink") archives to be loaded by the client. It is only supported by [hexed](/Hexing "wikilink") clients, which have been diffed with the option *\[Data\] Enable Multiple GRFs*. Official clients for main servers and [Sakray](/Sakray "wikilink") read data.grf, and rdata.grf or sdata.grf respectively.

File Format
-----------

The file follows default [INI file](/wikipedia:INI_file "wikilink") conventions. All entries are part of the section *data*. Each entry consists of a zero-based priority index as key name (0 = highest priority, 9 = lowest priority) and the GRF archive name as value. The file is stored in the same folder as the client it is supposed to be used by. Typical DATA.INI:

`[data]`
`0=yourserver.grf`
`1=rdata.grf`
`2=data.grf`

yourserver.grf
Normally the archive of your server is on the position 0 to override all other archives.

rdata.grf
Contains data from the test server, before it gets into data.grf, allowing to use pre-release content. For old Sakray clients this archive was called **sdata.grf**.

data.grf
The official main archive, which hosts the most vital data for the client. If it is missing, the client is most likely to crash during start-up.

Maximum amount of archives, that can be specified, is 10.

Other Names
-----------

You can also rename the **DATA.INI** file to any name that is 8 characters long (including the extension). Then, just edit your client with a [Hex Editor](/Hex_Editor "wikilink"). Find DATA.INI and replace with your new filename.

### Advanced name modification

This preferably requires an disassembler, I will use [OllyDbg](http://www.ollydbg.de/) 1.10 (I have not tested 2.0, yet) for this quick guide (I'll move it to wiki later, currently I have other stuff to do inside the wiki).

Start up OllyDbg, go to menu File -&gt; Open and find the client executable to patch. The loading and analysis process may take a while, but once the progress bar on the button is gone, right click into the code window, choose "Search for" and "All referenced text strings".

[<File:Datainiedit1.png>](/File:Datainiedit1.png "wikilink")

After another short while, all found and referenced strings are shown, you are interested in "DATA.INI" of course. Press "Home" key on your keyboard to get to the top of the list, then right click the list, and choose "Search for text". In the popup window, enter "data.ini" (without quotes), uncheck case-sensitive, check entire scope and click OK.

The selection inside the list should jump to a line with ".\\data.ini" inside it (unless the diff has changed since I last used diffs, a few years ago).

[<File:Datainiedit3.png>](/File:Datainiedit3.png "wikilink")

Press "Enter" key on your keyboard while the entry is highlighted, which should move you to the code position, where the string is used. Also as you could see in the list, the code shows, that there are two occurrences in the code, where ".\\data.ini" is used.

[<File:Datainiedit4.png>](/File:Datainiedit4.png "wikilink")

In my case, there is a lot of space after the text strings at offset 0x68dd38, so you just need to change the two occurrences to point there. To do that, mark one of the lines, that refer to ".\\data.ini" (PUSH 68DCF9 in this case) and hit "Space" key on your keyboard, which opens a assembling line. All you have to do is to update the value (68DCF9), to the offset, where you intend to place your new name (68DD38), after editing click "Assemble", then "Cancel". Repeat the same for the other line as well. The edited lines should turn red.

[<File:Datainiedit5.png>](/File:Datainiedit5.png "wikilink")

Now you could also add the string in there, but that can be done more easily inside the hex editor later. Note, that the offset inside OllyDbg (and most of the assemblers) is actual offset +0x400000, so you need to subtract the value, to get the correct offset in hex editor (in this case 0x68DD38 - 0x400000 = 0x28DD38). Remains to apply the changes, which is done by right clicking the code, choosing "Copy to executable" and "All modifications". You are asked, what you want to copy; unless you modified something else as well, clicking "Copy All" will do. Another window will popup, which is the modified file (title bar icon "D"). Right click it's contents and choose "Save file" and save the file under a name of your choice.

[<File:Datainiedit6.png>](/File:Datainiedit6.png "wikilink")

You can close OllyDbg now, remains setting the new name. As said before, you need to convert the disassembler offset, to an absolute one and go to that offset on a hex editor of your choice.

[<File:Datainiedit7.png>](/File:Datainiedit7.png "wikilink")

The first mark shows the old position of the name, which is no longer used, the second mark, is on the offset, where the new name is read. As you seen in this case, you have plenty of space. Make sure, that the name ends with a zero byte (00).

[Category:Client Configuration](/Category:Client_Configuration "wikilink") [Category:File Formats](/Category:File_Formats "wikilink")