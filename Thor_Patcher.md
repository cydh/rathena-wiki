---
title: Thor Patcher
permalink: /Thor_Patcher/
---

[Thor Patcher](/Thor_Patcher "wikilink") is designed with the client-side config file embed *inside* the patcher itself. Since it uses no extra DLLs, you may distribute 1 file to your players. This guide will not discuss how to setup a [Web Server](/wikipedia:Web_Server "wikilink").

Features
========

-   Pack into single/multi grf file \[0x200\]
-   Automatically generate GRF if not exists
-   RGZ support
-   Customizable skin
-   Multilingual base on user's OS region setting
-   Background music
-   No extra dll, not even config file is needed when distribute \[No conflict with other server\]
-   Embed config file and resource data (images for background/buttons)
-   Custom Buttons \[Hard limit &gt;2 billion, soft limit non-existence as in 2.6.2.68\]
-   Remote config file
-   Self update and client update \[Supports multi client exe update(Up to 255)\]

Files
=====

*Note: It is recommended that you use [Thor Patcher v.2.4.6.0](http://thor.aeomin.net/archive/Thor_Patcher%5B2.6.4.0%5D.7z) to avoid runtime errors.*

1.  Patcher folder contents:
    -   **Thor.exe** (*Patcher's executable file*)

2.  Tools folder contents:
    -   **CheckSum.exe** (*used to generate a CRC32 sum of the patcher and client exe*)
    -   **ThorGenerator.exe** (*used to make patches*)
    -   Sample skin files

3.  Web folder contents:
    -   a sample **notice.html**
    -   a sample **main.ini**

4.  Configuration folder contents:
    -   **ConfigGenerator.exe** (*used to add your config to the patcher exe*)
    -   **LanguageMap.ini** (*used to set different languages for the patcher exe*)
    -   **images** folder (*image files used for the patcher set in the config.ini*)
    -   a sample **config.ini**

Setup
=====

To set up your thor patcher, you need to go through the following steps:

-   make a skin
-   write a config.ini
-   write a language.ini (optional)
-   pack the config & skin into the patcher exe
-   write a main.ini
-   write a notice webpage
-   upload the main.ini & the notice to your webserver

Making a Skin
-------------

A Thor Patcher skin is divided into following parts:

1.  **Background** (*This is the main part of a skin*)
    -   supported formats
        -   jpg (no transparency)
        -   bmp (the very top-left pixel is used for transparency)
        -   partial transparency (.png) is not supported yet

2.  **Buttons**
    -   System Buttons:
        -   The typical buttons you see on every patcher:
        -   Start : starts the main client
        -   Cancel : cancels the update process
        -   Close : closes thor patcher
    -   Custom Buttons:


    see [guide](/#Custom_Buttons "wikilink")

3.  **Custom Notice Box**:

    see [guide](/#Custom_Notice_Box "wikilink")

4.  **Progressbar** (*Shows the patching progress*)
    -   Supported formats when use image based progress bar
        -   bmp
        -   jpg (crashes on 2.6.1.66)
        -   png (crashes on 2.6.1.66)

5.  **Status message** (*Displays the patcher status*)



You can change the size and the position of every element of the patcher, so there are almost no limits to what you can do - be creative. The easiest way to make a skin is to make a single photoshop file with layers for each part of the skin.

Writing the Config
==================

Config.ini contains the following lines:

\[Config:Main\]
---------------

-   RootURL='http://domain.com/patch/'
    -   The URL where you plan to store all data related to thor patcher. (If you wish to create a local one, use Xampp and its Apatch capability; then, put the Thor folder on "Xampp/htdocs" and access it through "127.0.0.1:80/<folder>".)
-   RemoteConfigFile='main.ini'
    -   The name of the 2nd part of the config (NOT the full path).
-   TimeOut=0
    -   This option enables you to control how long the patcher will try to connect to your webhost before giving up.
    -   Format: time in seconds.
    -   0 = Default value.
    -   **Don't** change this unless you know what you are doing! Might lead to patcher not patching.
-   StatusFile='server.dat'
    -   File that stores patch ID and possibly miscellaneous data in the future. Change it to fit your server.
-   DefaultGRF='YourRO.grf'
    -   The main GRF that your server uses. This GRF will will be patched if you left target GRF field blank during making .thor file or patch from GRF/GPF.
-   ClientEXE='Your RO.exe'
    -   The name of the executable that the patcher will launch after patching.
-   ClientParameter='-1sak1'
    -   The parameter thor uses when calling your client exe. Useful when you want your players to be fully patched. leave blank when not using.
    -   **Advice**: Change the parameter in your exe to something unique by hexing it, makes harder to bypass patching. Don't forget to change it in your config too.
-   FinishOnConnectionFailure=false
    -   The user can only exit if the patch fails and the setting is set to false. If set to true, the user can continue to launch the game if the patcher is unable to connect to your webserver. Setting to true may lead to gravity errors and crashes.

\[Config:Window\]
-----------------

-   AutoResize=true
    -   The size of the patcher changes depending on the size of the background image. True or false.
-   Style='none'
    -   Choose the style your window should have
    -   none : No border, window not resizable.
    -   single : Normal border, window not resizeable.
    -   sizeable : Normal border, window resizeable (would not work if windows_autosize = true).
-   Width=1
    -   Width of your patcher (in pixels). Would not work if *Autosize* = true
    -   Possible values:
        -   1 to 10000
-   Height=531
    -   Height of your patcher (in pixels). Would not work if *Autosize* = true
    -   Possible values:
        -   1 to 10000
-   DragHandling=true
    -   Should the user be able to move the patcher window by dragging on background? Note that when setting this to false, users would have to move window like every other GUI application, but they will unable to move when *Style* is set to *none*. True or false.
-   Background='images/bg.bmp'
    -   Your background image path.
    -   Relative to location of your config.ini
        -   Example: c:\\config.ini \*&gt; c:\\images\\bg.jpg
    -   Supported formats:
        -   JPG (no transparency)
        -   BMP (very first pixel at top left is choosed as transparent color)
        -   Partial Transparency (.png) is not supported at this moment
    -   Will be packed into the patcher.exe
-   FadeOnDrag=true
    -   Whether or not the window will create a fade effect when clicked and dragged (similar to window in RO). True or false.

\[Config:BGM\]
--------------

-   File=
    -   File name.
-   Loop=True
    -   Do you want the song to play over and over (AKA Loop)? True or false.
-   Volume=20
    -   How loud the song is. 1-100 in volume.
-   Directory=
    -   Where the song is located. When this field is set, patcher will randomly choose a music file in the specified directory. Note that *File* will be ignored in this case.

\[Config:Misc\]
---------------

-   Title='Your RO Patcher'
    -   Text displayed on the window title (if *Style* is not set to 'none'') and in taskbar.
-   HideProgressBarWhenFinish=false
    -   Should the progress bar vanish when the patching is done? True or false.

\[ProgressBar:bar1\]
--------------------

-   Width=1
    -   Width of the progress bar.
-   Height=1
    -   Height of the progress bar.
-   Left=1
    -   Number of pixels to the left.
-   Top=1
    -   Number of pixels away from the top.
-   BackColorStart=$009DEEEF
    -   The background color of the progress bar when it is patching.
-   BackColorEnd=$00C2F1F1
    -   The background color of the progress bar when it has finished patching.
-   FrontColorStart=$006ED5B0
    -   Foreground color of the progress bar when patching.
-   FrontColorEnd=$0080DDCA
    -   Foreground color when it is done.
-   FrontImage=
    -   Foreground image name. (NOTE: Image must be placed in Tools\\Images folder.)
-   BackImage=
    -   Background image name. (NOTE: Image must be placed in Tools\\Images folder.)
-   Hook='ProgressChange'
    -   Most likely something to do with programming and shouldn't be messed with.

\[Label:Status\]
----------------

-   AutoResize = false
    -   When set to true, this label will change its width depend on text size. True or false.
-   Width=369
    -   How wide the text area is in pixels. Ignored when *AutoResize* is true.
-   Height=
    -   How tall the text area is in pixels. Ignored when *AutoResize* is true.
-   Left=15
    -   How far from the right the text area is in pixels.
-   Top=498
    -   How far from the top the text area is in pixels.
-   Alignment='center'
    -   Text alignment. Can be center, left, or right.
-   FontColor=$000000
    -   Color of the text.
-   FontName = ''
    -   If you desire a different font to be displayed, you put the name here. Users must have the font installed in order to see the font, so downloaded fonts most likely won't be seen.
-   FontSize =
    -   Text size.
-   Text=''
    -   Text to be displayed at the bottom of the progress bar.
-   Hook='StatusChange'
    -   Programming related.

\[NoticeBox:Box0\]
------------------

-   Width=347
    -   Width of notice box.
-   Height=250
    -   Height of notice box.
-   Left=21
    -   How far from the left.
-   Top=217
    -   How far from the top.
-   URL='http://domain.com/patch/notice.html'
    -   URL to notice HTML file that will be displayed on startup, as long as the player is connected to the internet.

\[Button:Start\]
----------------

-   Default='images/start.png'
    -   Image of the button in normal state.
-   OnHover='images/start2.png'
    -   Image of the button when the user places the mouse cursor over it.
-   OnDown='images/start3.png'
    -   Image of the button when the user presses the button.
-   Left=1
    -   X coordinates of the button (in pixels).
    -   Counted from the left of the background image.
-   Top=1
    -   Y coordinates of the button (in pixels).
    -   Counted from the top of the background image.

\[Button:Exit\]
---------------

-   Default='images/exit.png'
    -   Image of the button in normal state.
-   OnHover='images/exit2.png'
    -   Image of the button when the user places the mouse cursor over it.
-   OnDown='images/exit3.png'
    -   Image of the button when the user presses the button.
-   Left=1
    -   X coordinates of the button (in pixels).
    -   Counted from the left of the background image.
-   Top=1
    -   Y coordinates of the button (in pixels).
    -   Counted from the top of the background image.

\[Button:Cancel\]
-----------------

-   Default='images/exit.png'
    -   Image of the button in normal state.
-   OnHover='images/exit2.png'
    -   Image of the button when the user places the mouse cursor over it.
-   OnDown='images/exit3.png'
    -   Image of the button when the user presses the button.
-   Left=1
    -   X coordinates of the button (in pixels).
    -   Counted from the left of the background image.
-   Top=1
    -   Y coordinates of the button (in pixels).
    -   Counted from the top of the background image.

Custom Buttons
--------------

<code>

    [Button:Name]
    Default='images/button1.png'
    OnHover='images/button2.png'
    OnDown='images/button3.png'

    Left=80
    Top=406
    Mode=1
    Action='http://example.com'

</code> Declares a new button

-   \[Button:Name\]
    -   Name or ID, must be unique for each and every button
-   Default='images/button1.png'
    -   image of the button on normal state
-   OnHover='images/button2.png'
    -   image of the button when mouse hovers it
-   OnDown='images/button3.png'
    -   image of the button when the user click on it
-   Left=80
    -   X coordinate of the button (in pixels)
    -   Counted from the left of the background image.
-   Top=406
    -   Y coordinate of the button (in pixels)
    -   Counted from the left of the background image.
-   Mode=1
    -   Functions of the button
        -   Possible Mode values:
            -   1 : Open URL
            -   2 : Open File/Program (remove the file extension or it won't work)
            -   3 : Displays a Message Box
            -   4 : Minimize window
            -   5 : Close Patcher
            -   6 : Makes this button as clone start button behavior
-   Action='http://example.com'
    -   Applies on modes 1-3

Custom Notice Box
-----------------

<code>

    [NoticeBox:Name]
    Width=347
    Height=250
    Left=21
    Top=217
    URL='http://domain.com/patch/notice.html'

</code> Declares the notice box

-   \[NoticeBox:Name\]
    -   Name or ID, must be unique for each and every notice boxes
-   Width=347
    -   Width of notice box.
-   Height=250
    -   Height of notice box.
-   Left=21
    -   How far from the left.
-   Top=217
    -   How far from the top.
-   URL='http://domain.com/patch/notice.html'
    -   URL to notice HTML file that will be displayed on startup, as long as the player is connected to the internet.

Writing a language.ini
======================

The language.ini is a fast way to switch your patcher's language without having to change the config file. It contains the same configuration lines as the language part of the config.ini

-   getting_info=Getting Information...
    -   is displayed when the patcher connects to the webhost
-   update_patcher=Updating Patcher...
    -   is displayed when the patcher updates itself
-   update_client=Updating Client...
    -   is displayed when the patcher upates the client
-   repacking=Repacking resource files...
    -   is displayed while the patcher repacks the grf
-   saving_res=Saving Resource...
    -   is displayed when the patcher generating table
-   getting_file=Getting file %s.
    -   is displayed when the patcher is downloading a file.
    -   "%s" will be replaced with the filename of the file
    -   if you want to use the "%" symbol in this message, write it as "%%"!
-   need_defrag=Data fragment reached %u%%, would you like to defrag now?
    -   is displayed when the grf fragmentation reaches a certain level (configured in the main.ini)
    -   "%u" will be replaced with a numeric value
    -   if you want to use the "%" symbol in this message, write it as "%%"!
-   defraging=Defragment in process...
    -   is displayed while the patcher defragments the grf
-   confirmation=Waiting Confirmation...
    -   is displayed while waiting for a reply from the user
-   client_locked=Client Application is locked
    -   is displayed when trying to patch a running client
-   failed_to_communicate=Failed to communicate with server
    -   is displayed when the patcher can't connect to the webhost
-   failed_to_get=Failed to get %s
    -   is displayed when the patcher cannot find a file on the webhost
    -   "%s" will be replaced by the filename of the file
    -   if you want to use the "%" symbol in this message, write it as "%%"!

Packing the Config Into the Patcher
===================================

Make sure the following files are in the same folder before proceeding:

-   config.ini
-   language.ini (optional)
-   Skin Files
-   ConfigGenerator.exe

Now, we are going to pack the config into the patcher.

-   Start ConfigGenerator
-   Select your copy of Thor.exe, located at the Patcher folder, by clicking "browse"
-   Press "Combine"

Writing the main.ini
====================

\[Main\]
--------

-   allow=true
    -   Allow patching or not.
-   Force_Start=false
-   policy_msg=

<!-- -->

-   file_url=http://domain.com/patch/data/
    -   the URL where you plan to save your patches in
        -   supports both HTTP and FTP
            -   HTTP: use the following format:
                -   http://domain.com/dir/
            -   FTP :
                -   connecting as anonymous:
                    -   ftp://domain.com/dir/
                -   connecting with user & pass:
                    -   ftp://username:password@domain.com:port/dir/
                    -   username is required if you want to use a password
                    -   if you don't specify the port, the default one will be used

\[Patch\]
---------

-   ClientSum=
-   PatcherSum=
    -   Can be obtained from CheckSum tool.

<!-- -->

-   ClientPath=
-   PatcherPath=
    -   Filename of patch file when update patcher/client. These files should store in the place with other patch files.

<!-- -->

-   PatchList=plist.txt
    -   Patch list file.

Writing the Notice Page
=======================

The archive includes a sample notice.html, but you can use other formats like .php, .asp etc.

By doing so, you also need change notice_file in **config.ini**

Common Problems
===============

-   Failed to communicate to server
    -   Make sure that you have connectivity and access to your webserver (i.e. ping, visiting the patch site)
    -   Check your config.ini &gt; RootUrl if it is pointing at the correct server
    -   Make sure that your main.ini can be accessed (i.e. trying it in your browser <http://yourdomain.com/patchs/main.ini> and doesn't give you an error)
        -   In-case you have "Forbidden" problems, rename your main.ini to main.txt and make sure that your config.ini &gt; RemoteConfigFile is also updated
        -   You can also check your file/folder permissions and set it to 755
-   Failed to get \*.thor
    -   Make sure that your RemoteConfigFile (i.e. main.ini) is configured file_url is pointing at the correct url (i.e. <http://yourdomain.com/patchs/data/>)
        -   Do not forget to put '/' at the end
    -   Make sure that your PatchList (i.e. plist.txt) is configured with the correct filename
    -   Make sure that you can download the patches manually (i.e. http or ftp download)
        -   If not you have a problem with webserver/url access
-   Runtime Error
    -   This is issue is about the ConfigGenerator being broken. It is recommended that you use [Thor Patcher v2.6.4.0](http://thor.aeomin.net/archive/Thor_Patcher%5B2.6.4.0%5D.7z)

See Also
--------

-   [GRF](/GRF "wikilink")

External Links
--------------

-   [Official Thor Patcher Homepage](http://thor.aeomin.net/)
-   [Official Thor Patcher Thread](http://www.eathena.ws/board/index.php?showtopic=171632)

[Category:Patchers](/Category:Patchers "wikilink")