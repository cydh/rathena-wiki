---
title: Ergo patcher
permalink: /Ergo_patcher/
---

[Category:Patchers](/Category:Patchers "wikilink")

Folder structure
----------------

<div style="background:#ececec">
MainFolder
-Patches
--Patches.XML
--PatchStatus.XML
-System
--Images
--Songs
-RO

</div>
Installation
------------

1. Extract the RAR-Archive
2. Copy your Ragnarok Online Client into the RO Folder (Directly)
3. Open the Config-File "**PatcherConfig.xml**"
and set all necessary XML Attributes (*See also "extended Configuration below"*)

<div style="background:#ececec">
<HTTPLink_Patcher_List><http://yourwebsite.com/Patches.xml></HTTPLink_Patcher_List>
<HTTPLink_Patches_Directory><http://yourwebsite.com/PatchesFolder/></HTTPLink_Patches_Directory>
<RagnarokEXEName>YourRagnarokOnline.exe</RagnarokEXEName>

</div>
Extended Configuration
----------------------

#### General Configuration

<div style="background:#ececec">
` `<InitRequired>`false`</InitRequired>
`  `<WindowTitle>`YourWindowTitle`</WindowTitle>
`  `<BackGroundPic>`214200.jpg`</BackGroundPic>
`  `<window_height>`450`</window_height>
`  `<window_width>`750`</window_width>
`  `<HTTPLink_Patcher_List>[`http://yourwebsite.com/Patches.xml`](http://yourwebsite.com/Patches.xml)</HTTPLink_Patcher_List>
`  `<HTTPLink_Patches_Directory>[`http://yourwebsite.com/PatchesFolder/`](http://yourwebsite.com/PatchesFolder/)</HTTPLink_Patches_Directory>
`  `<RagnarokEXEName>`YourRagnarokOnline.exe`</RagnarokEXEName>
`  `<MetroColor>`Lime`</MetroColor>
`  `<BoarderSize>`1`</BoarderSize>
`  `<GRFINI_Name>`Test`</GRFINI_Name>

</div>
<InitRequired> Ignore this.
<WindowTitle> Your windowtitle. ALphanumeric.
<BackGroundPic> Your patcher Background Image. Drop the Image into the System/Images folder.
<window_height> The height of the window. (Without the upper boarder)
<window_width> The width of the window. (Without the left/right boarder)
<MetroColor> Possible Colors are: **"Red", "Green", "Blue", "Purple", "Orange", "Lime", "Emerald", "Teal", "Cyan", "Cobalt", "Indigo", "Violet", "Pink", "Magenta", "Crimson", "Amber", "Yellow", "Brown", "Olive", "Steel", "Mauve", "Taupe", "Sienna"**
<BoarderSize> The size of the boarder around the patcher window in pixels. The color is the same as *MetroColor*

#### Buttons (Buttons List - *repeatable*')

This elements is a list of all buttons on the window. It is possible to repeat the buttons. (Add as much as you need)

<div style="background:#ececec">
` `<ButtonsSetter>
`    `<ButtonSettings>
`      `<Button_Title>`Website`</Button_Title>
`      `<OpenWebsite>[`http://www.youtube.com/`](http://www.youtube.com/)</OpenWebsite>
`      `<OpenProgramm>`setup.exe`</OpenProgramm>
`      `<ButtonBackGround>`background.jpg`</ButtonBackGround>
`      `<ButtonBackGround_Hover>`background_hover.jpg`</ButtonBackGround_Hover>
`      `<ButtonBackGround_Inactive>`background_inactive.jpg`</ButtonBackGround_Inactive>
`      `<Margin_Top>`210`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`50`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<DisableOnPatching>`true`</DisableOnPatching>
`      `<KillPatcherOnClick>`false`</KillPatcherOnClick>
`      `<KillMusikOnClick>`true`</KillMusikOnClick>
`      <Font>`
`        <font>Impact</font>`
`        <fontsize>12</fontsize>`
`        <color>#488864</color>`
`        <bold>true</bold>`
`      </Font>`
`   `</ButtonSettings>
`  `</ButtonsSetter>

</div>
This Element is a List of Buttons.
<Button_Title>Website</Button_Title>
This is the Button label text. (Shown on the Button)
<OpenWebsite><http://www.youtube.com/></OpenWebsite>
Any Website. (Will be opened in the standard Browser on click)
<OpenProgramm>setup.exe</OpenProgramm>
Any EXE in your RO/ Folder. (Like Setup.exe or your Client EXE)
**Note: If both are set the Button will open Both!
**

<ButtonBackGround>background.jpg</ButtonBackGround>
Drop the image into the System/Images folder.
<ButtonBackGround_Hover>background_hover.jpg</ButtonBackGround_Hover>
Drop the image into the System/Images folder.
<ButtonBackGround_Inactive>background_inactive.jpg</ButtonBackGround_Inactive>
This entry is only required for the Mute Music button..
<Margin_Top>210</Margin_Top>
The Y-Position
<Margin_Left>400</Margin_Left>
The X-Position
<Size_Width>50</Size_Width>
The width of the button in pixels.
<Size_Height>50</Size_Height>
The height of the button in pixels.
<DisableOnPatching>true</DisableOnPatching>
Should the button be disabled while patching?
<KillPatcherOnClick>false</KillPatcherOnClick>
Should the button also close the patcher when its clicked?
<KillMusikOnClick>true</KillMusikOnClick>
Should the button mute the Background Music?
&lt;Font&gt; &lt;font&gt;Impact&lt;/font&gt; The font of the button label. The font must be installed on the PC. &lt;fontsize&gt;12&lt;/fontsize&gt; The fontsize. &lt;color&gt;\#488864&lt;/color&gt; The Color or the Label text. In HEX. (See here for color examples: http://www.color-hex.com/) &lt;bold&gt;true&lt;/bold&gt; Should the Label be Bold true/false. &lt;/Font&gt;

In this Example I added a second button "Registration". Directly under the given button "Website".

<div style="background:#ececec">
` `<ButtonsSetter>
`    `<ButtonSettings>
`      `<Button_Title>`Website`</Button_Title>
`      `<OpenWebsite>[`http://www.youtube.com/`](http://www.youtube.com/)</OpenWebsite>
`      `<OpenProgramm>`setup.exe`</OpenProgramm>
`      `<ButtonBackGround>`background.jpg`</ButtonBackGround>
`      `<ButtonBackGround_Hover>`background_hover.jpg`</ButtonBackGround_Hover>
`      `<ButtonBackGround_Inactive>`background_inactive.jpg`</ButtonBackGround_Inactive>
`      `<Margin_Top>`210`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`50`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<DisableOnPatching>`true`</DisableOnPatching>
`      `<KillPatcherOnClick>`false`</KillPatcherOnClick>
`      `<KillMusikOnClick>`true`</KillMusikOnClick>
`      <Font>`
`        <font>Impact</font>`
`        <fontsize>12</fontsize>`
`        <color>#488864</color>`
`        <bold>true</bold>`
`      </Font>`
`   `</ButtonSettings>
`The second Button:`

<div style="background:#b0bca7">
`   `<ButtonSettings>
`      `<Button_Title>`Register`</Button_Title>
`      `<OpenWebsite>[`http://yourwebsite.com/register.php`](http://yourwebsite.com/register.php)</OpenWebsite>
`      `<OpenProgramm></OpenProgramm>
`      `<ButtonBackGround>`background.jpg`</ButtonBackGround>
`      `<ButtonBackGround_Hover>`background_hover.jpg`</ButtonBackGround_Hover>
`      `<ButtonBackGround_Inactive>`background_inactive.jpg`</ButtonBackGround_Inactive>
`      `<Margin_Top>`250`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`50`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<DisableOnPatching>`true`</DisableOnPatching>
`      `<KillPatcherOnClick>`false`</KillPatcherOnClick>
`      `<KillMusikOnClick>`true`</KillMusikOnClick>
`      <Font>`
`        <font>Impact</font>`
`        <fontsize>12</fontsize>`
`        <color>#488864</color>`
`        <bold>true</bold>`
`      </Font>`
`   `</ButtonSettings>
`  `</ButtonsSetter>

</div>
</div>
#### Webbrowsers (Webbrowser List - *repeatable*')

[<File:Ergo_Patcher_Webbrowser_Element.PNG>‎](/File:Ergo_Patcher_Webbrowser_Element.PNG‎ "wikilink")

<div style="background:#ececec">
` `<Webbrowsers>
`    `<WebBrowserSettings>
`      `

<HTML>
<http://google.de>

</HTML>
<Margin_Top>3</Margin_Top>
<Margin_Left>3</Margin_Left>
<Size_Width>380</Size_Width>
<Size_Height>270</Size_Height>
</WebBrowserSettings>
</Webbrowsers>

</div>
The webbrowser element could be used to show a patch history. It opens a website and shows it on the patcher window.
NOTE: The Sliders will be shown as soon as the content of the website is to big for the webbrowser. If the website is just as big as the webbrowser the sliders wont be there.

#### Labels (Labels List - *repeatable*')

<div style="background:#ececec">
` `<LabelSetting>
`    `<LabelSettings>
`      `<Text>`Username:`</Text>
`      `<Margin_Top>`15`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`200`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Hidden>`false`</Hidden>
`      `<LabelFont>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</LabelFont>
`    `</LabelSettings>
`  `</LabelSetting>

</div>
Labels are just a text on the patcher window. Some labels are preset and the text will be auto set by the patcher. (Loadingbar- Labels)
The "Hidden" entry is for those labels which are preset by the patcher. (If don't wish to show the Downloading file for example.)

#### Loading Bars (Fixed Element - *not Repeatable*')

[<File:Ergo_Pather_Loading_Bars_and_Labels.PNG>‎](/File:Ergo_Pather_Loading_Bars_and_Labels.PNG‎ "wikilink")

<div style="background:#ececec">
` `<LoadingBarSetter>
`  `
`   `<CompleteProgressBar>
`      `<Margin_Top>`365`</Margin_Top>
`      `<Margin_Left>`15`</Margin_Left>
`      `<Size_Width>`720`</Size_Width>
`      `<Size_Height>`10`</Size_Height>
`      `<color>`#488864`</color>
`    `</CompleteProgressBar>
`    `
`   `<SingleFileProgressBar>
`      `<Margin_Top>`390`</Margin_Top>
`      `<Margin_Left>`15`</Margin_Left>
`      `<Size_Width>`720`</Size_Width>
`      `<Size_Height>`10`</Size_Height>
`      `<color>`#488864`</color>
`    `</SingleFileProgressBar>
`    `
`   `<CurrentFileLabel>
`      `<Text>`LoadingBarLabel`</Text>
`      `<Margin_Top>`395`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`200`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Hidden>`false`</Hidden>
`      `<LabelFont>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</LabelFont>
`    `</CurrentFileLabel>
`    `
`   `<DownloadSpeedLabel>
`      `<Text>`0 kb/s`</Text>
`      `<Margin_Top>`395`</Margin_Top>
`      `<Margin_Left>`600`</Margin_Left>
`      `<Size_Width>`200`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Hidden>`false`</Hidden>
`      `<LabelFont>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</LabelFont>
`    `</DownloadSpeedLabel>
`    `
`   `<PercentageLabel>
`      `<Text>`Your Label Text`</Text>
`      `<Margin_Top>`370`</Margin_Top>
`      `<Margin_Left>`15`</Margin_Left>
`      `<Size_Width>`300`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Hidden>`false`</Hidden>
`      `<LabelFont>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</LabelFont>
`    `</PercentageLabel>
`    `
`   `<PercentageLabelSingleFile>
`      `<Text>`Your Label Text`</Text>
`      `<Margin_Top>`395`</Margin_Top>
`      `<Margin_Left>`15`</Margin_Left>
`      `<Size_Width>`50`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Hidden>`false`</Hidden>
`      `<LabelFont>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</LabelFont>
`    `</PercentageLabelSingleFile>
`    `
`   `<ProzessedFilesLabel>
`      `<Text>`Your Label Text`</Text>
`      `<Margin_Top>`370`</Margin_Top>
`      `<Margin_Left>`320`</Margin_Left>
`      `<Size_Width>`300`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Hidden>`false`</Hidden>
`      `<LabelFont>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</LabelFont>
`    `</ProzessedFilesLabel>
`    `
`   `<ProzessInfoLabel>
`      `<Text>`Your Label Text`</Text>
`      `<Margin_Top>`160`</Margin_Top>
`      `<Margin_Left>`300`</Margin_Left>
`      `<Size_Width>`300`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Hidden>`false`</Hidden>
`      `<LabelFont>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</LabelFont>
`    `</ProzessInfoLabel>
`  `</LoadingBarSetter>

</div>
#### SSO Login (Fixed Element - *not Repeatable*')

To use this feature you need to hex your client exe with following patches: *skip license Screen*' - not needed but nice
*skip Service Selection Screen*' - also not required but nice to have
*use SSO Login Packet*' - Required
[<File:Ergo_Pather_SSO-Login.PNG>](/File:Ergo_Pather_SSO-Login.PNG "wikilink")

<div style="background:#ececec">
<SSOLoginSetter>
`    `<EnableSSOLoginPackage>`true`</EnableSSOLoginPackage>
`    `<RagOrSakParameter>`-1rag1`</RagOrSakParameter>
`    `<ClientinfoXMLFileName>`clientinfo.xml`</ClientinfoXMLFileName>
`    `<CheckLogin>`true`</CheckLogin>
`    `<LinkToPHPCheckLogin>[`http://kasuminator.bplaced.net/test.php`](http://kasuminator.bplaced.net/test.php)</LinkToPHPCheckLogin>
`    `<LoginCheckImage>
`      `<ToggleActive>`correct.png`</ToggleActive>
`      `<ToggleInactive>`wrong.png`</ToggleInactive>
`      `<Margin_Top>`35`</Margin_Top>
`      `<Margin_Left>`705`</Margin_Left>
`      `<Size_Width>`25`</Size_Width>
`      `<Size_Height>`25`</Size_Height>
`    `</LoginCheckImage>
`    `<PasswordCheckImage>
`      `<ToggleActive>`correct.png`</ToggleActive>
`      `<ToggleInactive>`wrong.png`</ToggleInactive>
`      `<Margin_Top>`85`</Margin_Top>
`      `<Margin_Left>`705`</Margin_Left>
`      `<Size_Width>`25`</Size_Width>
`      `<Size_Height>`25`</Size_Height>
`    `</PasswordCheckImage>
`    `<LoginButton>
`      `<Button_Title>`Start`</Button_Title>
`      `<OpenWebsite>`A Website.`</OpenWebsite>
`      `<OpenProgramm>`An EXE within Your RO Folder`</OpenProgramm>
`      `<ButtonBackGround>`background.jpg`</ButtonBackGround>
`      `<ButtonBackGround_Hover>`background_hover.jpg`</ButtonBackGround_Hover>
`      `<ButtonBackGround_Inactive>`background_inactive.jpg`</ButtonBackGround_Inactive>
`      `<Margin_Top>`125`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`50`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<DisableOnPatching>`true`</DisableOnPatching>
`      `<KillPatcherOnClick>`false`</KillPatcherOnClick>
`      `<KillMusikOnClick>`true`</KillMusikOnClick>
`      `<Font>
`        `<font>`Impact`</font>
`        `<fontsize>`12`</fontsize>
`        `<color>`#488864`</color>
`        `<bold>`true`</bold>
`      `</Font>
`    `</LoginButton>
`    `<LoginInput>
`      `<Margin_Top>`35`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`300`</Size_Width>
`      `<Size_Height>`25`</Size_Height>
`      `<PreSetValue>`kasuminator`</PreSetValue>
`    `</LoginInput>
`    `<PasswordInput>
`      `<Margin_Top>`85`</Margin_Top>
`      `<Margin_Left>`400`</Margin_Left>
`      `<Size_Width>`300`</Size_Width>
`      `<Size_Height>`25`</Size_Height>
`      `<PreSetValue>`ImInput`</PreSetValue>
`    `</PasswordInput>
`    `<RememberUsername>
`      `<Hidden>`false`</Hidden>
`      `<Margin_Top>`115`</Margin_Top>
`      `<Margin_Left>`720`</Margin_Left>
`      `<Size_Width>`50`</Size_Width>
`      `<Size_Height>`50`</Size_Height>
`      `<Remember>`true`</Remember>
`    `</RememberUsername>
`  `</SSOLoginSetter>

</div>
===== Checking Username an Password before Login ==== This function will call a .php on your server. It sends the Username and Password to this php.
The PHP should check if $Username and $Password is correct and Respond with "PASSWORD:OK and LOGIN:OK".
Example Responses:
Password Correct but Username wrong: (both will should show up as wrong to prevent guessing)
PASSWORD:WRONG
LOGIN:WRONG
Login correct password wrong:
PASSWORD:WRONG
LOGIN:OK
Login correct and password correct:
PASSWORD:OK
LOGIN:OK
This PHP Example would always respond that both are correct:

<div style="background:#ececec">
<?php<br>
`    $Username = $_POST["username"];`
`     $Password = $_POST["password"];`
`     echo "PASSWORD:OK";`
`     echo "LOGIN:OK";`
`?>`

</div>
**Warning! I do not recommending using this PHP! Its just an example!**
How to enable that function:
<CheckLogin>true</CheckLogin> Set this to true.
<LinkToPHPCheckLogin><http://yourwebsite.com/checklogin.php></LinkToPHPCheckLogin> Add here the link to the PHP.
Setting both of this elements will also enable the icons which show the player what went wrong:

<div style="background:#ececec">
`   `<LoginCheckImage>
`      `<ToggleActive>`correct.png`</ToggleActive>
`      `<ToggleInactive>`wrong.png`</ToggleInactive>
`      `<Margin_Top>`35`</Margin_Top>
`      `<Margin_Left>`705`</Margin_Left>
`      `<Size_Width>`25`</Size_Width>
`      `<Size_Height>`25`</Size_Height>
`    `</LoginCheckImage>
`    `<PasswordCheckImage>
`      `<ToggleActive>`correct.png`</ToggleActive>
`      `<ToggleInactive>`wrong.png`</ToggleInactive>
`      `<Margin_Top>`85`</Margin_Top>
`      `<Margin_Left>`705`</Margin_Left>
`      `<Size_Width>`25`</Size_Width>
`      `<Size_Height>`25`</Size_Height>
`    `</PasswordCheckImage>

</div>
#### Background Music

**Note: All Buttons can mute the Music.**
Drop a song into the folder System/Songs/

<div style="background:#ececec">
<BackgroundMusik>
<PlayMusik>true</PlayMusik>
<RepeatPlayList>true</RepeatPlayList>
<Muted>true</Muted>
<MuteButton>
<Button_Title />
<OpenWebsite>A Website.</OpenWebsite>
<OpenProgramm>An EXE within Your RO Folder</OpenProgramm>
<ButtonBackGround>sound.png</ButtonBackGround>
<ButtonBackGround_Hover />
<ButtonBackGround_Inactive>mute.png</ButtonBackGround_Inactive>
<Margin_Top>320</Margin_Top>
<Margin_Left>675</Margin_Left>
<Size_Width>50</Size_Width>
<Size_Height>50</Size_Height>
<DisableOnPatching>true</DisableOnPatching>
<KillPatcherOnClick>true</KillPatcherOnClick>
<KillMusikOnClick>true</KillMusikOnClick>
&lt;Font&gt; &lt;font&gt;Impact&lt;/font&gt; &lt;fontsize&gt;12&lt;/fontsize&gt; &lt;color&gt;\#FF000000&lt;/color&gt; &lt;bold&gt;true&lt;/bold&gt; &lt;/Font&gt;
</MuteButton>
<Songs>
<Song>
<FileName>YourSong.mp3</FileName>
</Song>
<Song>
<FileName>SeconfSong.mp3</FileName>
</Song>
</Songs>
</BackgroundMusik>

</div>
Adding Patches
--------------

Create a GRF with all items/files you want to update in your client.
Upload this GRF File on your server.. the path should be set here:
<HTTPLink_Patches_Directory><http://yourwebsite.com/PatchesFolder/></HTTPLink_Patches_Directory>
Now add the patch to the patchlist.

<div style="background:#ececec">
<?xml version="1.0" encoding="utf-8"?>
<PatchList xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<patches>
<Patch>
<FileName>patchmecom.grf</FileName>
<Date>2005-01-01T00:00:00</Date>
<Destination>basegrf.grf</Destination>
</Patch>
<Patch>
<FileName>patchmecom2.grf</FileName>
<Date>2005-01-01T00:00:00</Date>
<Destination>basegrf.grf</Destination>
</Patch>
<Patch>
<FileName>patch_override.grf</FileName>
<Date>2005-01-01T00:00:00</Date>
<Destination>data/</Destination>
</Patch>
<Patch>
<FileName>patch_overrideme.grf</FileName>
<Date>2005-01-01T00:00:00</Date>
<Destination>data/</Destination>
</Patch>
</patches>
</PatchList>

</div>
One patch should look like this:
<Patch>
<FileName>yourpatch.grf</FileName>
<Date>2016-03-01T00:00:00</Date>
<Destination>data/</Destination>
</Patch>
The Date is very important. The patcher decides witch patch to do first by the date!
The format is: JJJJ-MM-DDTHH-MM-SS (JEAR-MONT-DAYT-HOUR-MINUTE-SECOND)
The Destination can be a folder insinde your RO Folder. The patcher will then extract all files into the destination folder!
Leave <Destination></Destination> Empty if you want to update files inside the Mainfolder RO/.
If you wish to update a GRF inside your ro folder set <Destination>rdata.grf</Destination> to an GRF File (in this example our patch will be added to rdata.grf).
The FileName should never be used twice!
This patcher also supports .ZIP Files as packeges to extract. (Your user would download only the patcher. The patcher himself downloads the complete client!)
Now upload the Patches.XML on your server. The path should be set here: <HTTPLink_Patcher_List><http://yourwebsite.com/Patches.xml></HTTPLink_Patcher_List>
