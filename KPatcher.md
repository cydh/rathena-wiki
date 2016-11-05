---
title: KPatcher
permalink: /KPatcher/
---

**KPatcher** is a Ragnarok Online auto-patcher, written in Embarcadero C++ Builder XE2. It was originally developed in the Russian eAthena community[1](http://www.eathena.ws/board/index.php?showtopic=216716), but later released as multi-language version[2](http://www.eathena.ws/board/index.php?showtopic=247878), currently supporting Russian, English, Spanish, Japanese, Chinese, Portuguese and Indonesian, with further languages being planned. It consists of the patcher binary itself and a tool for creating configuration. It works on Windows 2000, Windows XP and higher.

Features
--------

-   Fast merge GRF/GPF files;
-   Defragment GRF file;
-   Delete files from the GRF on the mask;
-   Deleting files from your client on a mask;
-   Unpack the RGZ/RAR archives;
-   The ability to patch any GRF file in the folder with patcher;
-   Unique auto update;
-   Support for the official patch server;
-   Simple skinning;
-   Remote file settings and auto update;
-   Support for custom buttons.

Files
-----

1.  Patcher folder contents:
    -   **KPatcher.exe** (*Patcher's executable file*)
    -   **ConfigTool.exe** (*used to add your config, custom icon file and generate a CRC32 sum of any file*)
    -   Simple config file *Example.kpsf*
    -   Simple skin files
    -   Simple icon file
    -   Language files

2.  Web folder contents:
    -   Simple *kpatcher.php*
    -   Simple remote settings *settings.ini*
    -   Simple auto update *update.ini*
    -   Simple patch lists *plist.ini* and old format *plist.plt*

Configuration
-------------

To get a workable version of the patcher you will need to follow a few simple steps:

1.  Make a skin (*optional*);
2.  Write own *.kpsf* file using *Example.kpsf*;
3.  Using **ConfigTool.exe** pack the own *.kpsf* file into the patcher exe;
4.  Write *settings.ini*;
5.  Write own *.php* file using as example *kpatcher.php*;
6.  Upload *.kpsf* and *.php* files to your webserver;
7.  Create patch list and upload to your webserver.

### Skins

To control the skins patcher uses a special file style.ini, the structure of which we analyze.

1.  The dimensions of the main window, buttons, and information lines are changed automatically, depending on the content;
2.  For skin use \*.bmp or \*.png with transperence color $ff00ff, all other formats without transperence;
3.  For buttons use \*.png with AlphaTransperence.
4.  All elements of the skin using the same parameters to specify the size and spacing:
    -   Left - Number of pixels to the left;
    -   Top - Number of pixels away from the top;
    -   Width - Width of the element;
    -   Height - Height of the element;

5.  All the buttons has at least three states, the buttons that trigger a specific action have a additional state:
    -   Active - button is active and can be pressed;
    -   Inactive - button is not active at all (only for buttons that trigger the feature);
    -   Hover - pointer hovers over the button;
    -   Pressed - button is pressed, the action will be taken after releasing the button.

6.  Text elements (**\[Status\]** and **\[Info\]**) has two of its parameters which are responsible for the color and font size:
    -   Color - color of the text;
    -   FontSize - text size.

### Patch List

The patch list is a simple text file, which uses one line for each patch. Patches are distinguished by a unique id (abbreviated with **PID** in examples below), which must increase with each patch, usually starting with 1. Lines beginning with // are considered a comment and ignored, which can also be used for disabling patches. Following patch types exist:

-   **PAU**
    Specifies patch for updating the patcher.
        PAU:CRC:patcher.upd

    CRC is the checksum of the new patcher executable **patcher.upd**. If the CRC of the current patcher differs, update of the patcher will occur. Might appear everywhere in the patch list, but preferably at the beginning.

-   **GRF**
    Specifies a patch, which will be applied to a GRF archive. This type has two forms; the first applies the patch to the main archive as specified in settings, the other applies the patch to the GRF archive specified before the type.
        PID:GRF:2010-09-30palettefix.gpf

        PID:adata.grf:GRF:2010-09-30palettefix.gpf

-   **ARCH**
    Specifies, that the patch is a ZIP archive, which will be extracted into the folder, where the patcher resides, including the folder structure stored inside the archive.
        PID:ARCH:newclient.zip

-   **GDF**
    Specifies a file, to be removed from the main GRF archive.
        PID:GDF:data\clientinfo.xml

    This type also accepts [regular expressions](http://en.wikipedia.org/wiki/Regular_expression), such as deleting all palette files (\*.pal), would be:

        PID:GDF:^.+\.pal$

-   **CDF**
    Specifies a local file to be deleted from the folder, where the patcher resides.
        PID:CDF:dinput.dll

#### Example

`PAU:CRC:patcher.upd`
`//1:GRF:pal.gpf`
`2:GRF:rdata.grf`
`3:ARCH:lib.zip`
`//4:ARCH:data.zip`
`5:GDF:data\clientinfo.xml`
`6:CDF:dinput.dll`
`7:name.grf:GRF:patch.grf`

External Links
--------------

-   [Official KPatcher Topic (English)](http://www.eathena.ws/board/index.php?showtopic=247878)
-   [Official KPatcher Topic (Russian)](http://www.eathena.ws/board/index.php?showtopic=216716)

[Category:Patchers](/Category:Patchers "wikilink")