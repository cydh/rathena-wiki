---
title: Triad Patcher
permalink: /Triad_Patcher/
---

**Triad Patcher** is a Ragnarok Online auto-patcher, written in Borland Delphi 6 and currently available in French and English. It is divided into the patcher executable itself and tools for creating configuration and patches. Works on all 32-bit Windows versions, Windows Vista and Windows 7 may require running as administrator, though.

Features
--------

The patcher is able to patch local files, as well as multiple [GRF](/GRF "wikilink") archives (only version 2.00 is supported). The user interface offers displaying of patch news, full skinning with transparency support, support for additional languages, background music during patch process and usage of a static or dynamic banner in formats BMP, JPG, PNG and SWF. It has the capability to update itself and the configuration automatically. The patches are provided using a proprietary file format (Triad Patcher Patch, .tpp).

Initial Setup
-------------

After extracting the release archive, following steps are required, before the patcher is ready for distribution:

-   Configuration of the patcher parameters, skin, language and patches.
-   Setting-up a web-space for patch list, patch news and patch files. The last one being preferably in a sub-directory of the location, where patch list and news reside to avoid clutter. Details on installing and configuring a web-server and/or web-space are beyond the scope of this article.

Then completed, files **config.tpc**, **Triad Patcher.exe** and **GRF.dll** are distributed to the players as part of the other client files.

Configuration
-------------

Most of the configuration is required to be done only once, unless something client-side or connection-related requires changes. After setting all options in **config.ini** and **languages.ini**, and preparing related files such as skin and background music, everything is packed into a single file called **config.tpc** using a included tool located in **Configurator\\Triad Configurator.exe**. The tool is pretty straight-forward, thus does not require further explanation. Configuration files should be kept after building the config, as there are no means to decompile it. Default configuration can be found in directory **Configurator\\Default**.

All mentioned configuration files follow the schematics of an [INI file](http://en.wikipedia.org/wiki/INI_file).

### Configuration (config.ini)

This file defines the main aspects of the patcher's behavior, such as visual and aural appearance and remote resource locations.

#### Section \[baseoptions\]

The section **baseoptions** recognizes following values:

language
Defines the interface language. Value is one of the section names in **language.ini**.

about_lang
Defines the interface language for the "About" window. Can be either 0 (French) or 1 (English).

about_header
Custom text in the about box, which appears before other credits. Character | can be used as newline.

bmpskin_path
Specifies the path for *bmpskin_file*. If blank, location of **config.ini** is assumed.

bmpskin_file
Sets a file to be used as skin. Magenta () is used as transparency color. Position of skin elements is defined in section *skinmap*.

banner_width
Defines the width in pixels of a banner, if any. The height is automatically set to 88.

banner_path
Specifies the path for *banner_file*. If blank, location of **config.ini** is assumed.

banner_file
Sets a file to be used as skin.

banner_type
Specifies the type of the file specified in *banner_file*. Can be 0 (no banner), 1 (SWF), 2 (BMP), 3 (JPG) or 4 (PNG).

bgm_enabled
Defines, whether background music should be played (1) or not (0).

bgm_file
MP3 file to be used as background music.

btnsnd_enabled
Specifies, whether click/button sounds should be played (1) or not (0).

create_log
Whether a debug log file should be created by the patcher (1) or not (0). Note, that the logs are only available in French.

#### Section \[urls\]

The section **urls** recognizes following values:

news
Absolute URL to the patch news to display.

register
Absolute URL to the page, which is used for registering. It is displayed in the "About" dialog.

patchs_list
Absolute URL to the patch list.

exec_file
File name of the client to execute, when "Start" is clicked.

exec_args
Parameters to pass to the client set in *exec_file*, like 1rag1 or 1sak1. Can be blank.

#### Section \[skinmap\]

The section **skinmap** specifies meaning of areas in file defined by *bmpskin_file*.

-   Values *body_\** represent the background image.
-   Values *button_start_\**, *button_quit_\** and *button_about_\** represent areas used for buttons (normal state).
-   Finally, values *button_startb_\**, *button_quitb_\** and *button_aboutb_\** represent areas, which are used for buttons when the mouse pointer hovers them.

For an example, check the default **skin.bmp** together with default **config.ini**.

#### Section \[interface\]

The section **interface** specifies the size of the patcher window and layout of buttons, progress bar and patch news.

-   Values *body_\** set the patcher window size.
-   Values *webbrowser_\** specify the position and dimensions of the patch news.
-   All width and height values should be same as specified in section *skinmap*. If larger values are specified, the surplus space is rendered in white.
-   The "About" button must be always visible, thus at least 5x5 in size.

#### Section \[interface_options\]

The section **interface_options** recognizes following values:

button_start_enabled
Specifies, whether the "Start" button should be enabled (1) or not (0).

button_quit_enabled
Specifies, whether the "Close" button should be enabled (1) or not (0).

progressbar_enabled
Specifies, whether the progress bar should be displayed (1) or not (0).

webbrowser_enabled
Specifies, whether the patch news should be displayed (1) or not (0).

Note, that the "About" button cannot be disabled.

#### Section \[progressbar_webbrowser\]

The section **progressbar_webbrowser** recognizes following values:

progressbar_bordercolor
Specifies the border color for the progress bar.

progressbar_backcolor
Specifies the background color for the progress bar.

progressbar_forecolor
Specifies the bar color for the progress bar.

webbrowser_bordercolor
Specifies the border color of the browser.

All color values are written as hexadecimal [RGB](http://en.wikipedia.org/wiki/RGB) color values in format RRGGBB. For example full red being written as FF0000.

#### Section \[textfont\]

The section **textfont** recognizes following values:

button_name
Font name to use for button text.

button_size
Font size to use for button text.

button_color
Color to use for button text.

button_bold
Whether the text in buttons should be bold (1) or regular (0) type.

body_name
Font name to use for status text.

body_size
Font size to use for status text.

body_color
Color to use for status text.

body_bold
Whether the text in status line should be bold (1) or regular (0) type.

For *button_name* and *body_name* use only fonts, which can be expected on every Windows installation, otherwise it might lead to undesired or unreadable results. All color values are written as hexadecimal **RGB** color values in format RRGGBB. For example full red being written as FF0000.

#### Example

`[baseoptions]`
`language = english`
`about_lang = 1`
`about_header = MyRO.ORG (http://myro.org/)`
`bmpskin_path =`
`bmpskin_file = skin.bmp`
`banner_width = 545`
`banner_path =`
`banner_file =`
`banner_type = 0`
`bgm_enabled = 0`
`bgm_file = myBGM.mp3`
`btnsnd_enabled = 1`
`create_log = 0`
`[urls]`
`news = http://myro.org/p/news.htm`
`register = http://myro.org/register/`
`patchs_list = http://myro.org/p/patchlist.ini`
`exec_file = myro.exe`
`exec_args =`
`[skinmap]`
`body_left = 0`
`body_top = 0`
`body_width = 545`
`body_height = 469`
`button_start_left = 0`
`button_start_top = 0`
`button_start_width = 0`
`button_start_height = 0`
`button_quit_left = 0`
`button_quit_top = 0`
`button_quit_width = 0`
`button_quit_height = 0`
`button_about_left = 0`
`button_about_top = 0`
`button_about_width = 0`
`button_about_height = 0`
`button_startb_left = 1`
`button_startb_top = 470`
`button_startb_width = 84`
`button_startb_height = 22`
`button_quitb_left = 86`
`button_quitb_top = 470`
`button_quitb_width = 84`
`button_quitb_height = 22`
`button_aboutb_left = 171`
`button_aboutb_top = 470`
`button_aboutb_width = 84`
`button_aboutb_height = 22`
`[interface]`
`body_width = 545`
`body_height = 469`
`button_start_left = 395`
`button_start_top = 69`
`button_start_width = 84`
`button_start_height = 22`
`button_quit_left = 395`
`button_quit_top = 90`
`button_quit_width = 84`
`button_quit_height = 22`
`button_about_left = 395`
`button_about_top = 111`
`button_about_width = 84`
`button_about_height = 22`
`progressbar_left = 18`
`progressbar_top = 438`
`progressbar_width = 509`
`progressbar_height = 18`
`webbrowser_left = 17`
`webbrowser_top = 161`
`webbrowser_width = 511`
`webbrowser_height = 252`
`[interface_options]`
`button_start_enabled = 1`
`button_quit_enabled = 1`
`progressbar_enabled = 1`
`webbrowser_enabled = 1`
`[progressbar_webbrowser]`
`progressbar_bordercolor = C0C0C0`
`progressbar_backcolor = FFFFFF`
`progressbar_forecolor = C0C0C0`
`webbrowser_bordercolor = C0C0C0`
`[textfont]`
`button_name = MS Sans Serif`
`button_size = 8`
`button_color = 000000`
`button_bold = 0`
`body_name = MS Sans Serif`
`body_size = 8`
`body_color = 000000`
`body_bold = 0`

### Interface Language (languages.ini)

This file specifies to the patcher all available languages, which can be enabled in **config.ini**. Only one language can be active at a time, but the configuration can be distributed in different flavors; each with different language set. Each section name corresponds to the language name being set, see *baseoptions* -&gt; *language* above for details.

In each language section, following values are recognized:

button_start
Text for button "Start". Can be empty, for example when the text is part of the skin.

button_quit
Text for button "Close". Can be empty, for example when the text is part of the skin.

button_about
Text for button "About". Can be empty, for example when the text is part of the skin.

progressinfo_msg1
Message, when the associated client fails to start.

progressinfo_msg2
Message, when patch news are being downloaded.

progressinfo_msg3
Message, when patch news finished downloading.

progressinfo_msg4
Message, when patch list is being downloaded.

progressinfo_msg5
Message, when patch list finished downloading and is about being processed.

progressinfo_msg6
Message, when patches are about being downloaded.

progressinfo_msg7
Message, when there are no patches available at time being.

progressinfo_msg8
Message, when patches finished downloading and are about being applied.

progressinfo_msg9
Message, when patches were applied.

progressinfo_msg10
Message, when a patch is being downloaded.

progressinfo_msg11
Message, when patches are applied to a GRF archive.

progressinfo_msg12
Message, when a GRF archive is being repacked.

### Patch List

This configuration file is the only one, which is not part of **config.tpc**, but is hosted remotely, on a web-space. It specifies, whether the patcher is allowed to patch and start the client, and what patches are to be applied. The name of this file can be chosen in **config.ini**, in section *urls* -&gt; *patchs_list*.

#### Section \[options\]

The section **options** recognizes following values:

deny_getpatch
Specifies, whether patching is allowed (0) or not (1).

deny_play
Specifies, whether the associated client can be started (0) or not (1).

#### Section \[patchs\]

Section **patchs** contains a list of all available patches, where the key name specifies the absolute location of the patch file, while the value enables (1) or disables (0) given patch. Note, that patches are not identified by any patch ID, as usually done, but by their base name, thus it is preferable to start the name with their release date, followed by keyword, which describes the patch, like **2010-09-21palettefix.tpp**.

#### Example

`[options]`
`deny_getpatch = 0`
`deny_play = 0`
`[patchs]`
`; fix for bards looking strange with some cloth colors`
`http://myro.org/patches/2010-09-21palettefix.tpp = 1`
`; disabled, because it is broken`
`http://myro.org/patches/2010-09-22newclient.tpp = 0`
`; fix for crash in party window`
`http://myro.org/patches/2010-09-25newclient.tpp = 1`

Creating Patches
----------------

Patches are created with a included tool located in **Packer\\Triad Packer.exe** in the original distribution. This tool allows to bundle multiple patches into a single patch, which uses a proprietary format, with extension **.tpp**. Note, that there are no means to extract the patch after it has been created, except using it with the patcher. After starting the tool, a window with four buttons can be seen, which have following functions:

Ajouter / Add
Adds GPF patches and local files to the compile list. If a GPF file is selected, destination archive must be specified (ex. adata.grf), otherwise for local files, their final destination must be set (ex. myfolder\\myfile.ext).

Empacter / Pack
Compiles the added patches into a triad patch file.

Sauvegarder / Save
Save the current compile list into a triad patch list, which can be loaded later for either reusage or resuming the creating of a patch. The patch list has the extension **.tpl** and is only meaningful to the packer.

Ouvrir / Open
Opens a previously saved triad patch list. If there already was a filled compile list, it is discarded.

Finally after creating the triad patch, it has to be added to the patch list into the section \[patchs\] and uploaded to the location specified.

See Also
--------

-   [GRF](/GRF "wikilink")

External Links
--------------

-   [Official Triad Patcher Homepage (French)](http://triad.nitroconcept.net/)
-   [Official Triad Patcher Homepage (English)](http://triad.nitroconcept.net/index_eng.php)

[Category:Patchers](/Category:Patchers "wikilink")