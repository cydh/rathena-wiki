---
title: Hexing
permalink: /Hexing/
---

As **hexing** is considered the process of modifying raw contents of a file on byte-level with a [hex editor](/Hex_Editor "wikilink"), regardless of the actual purpose of the file (text, image or another application). Such modifications may require exact knowledge of the files' format for the modification to succeed, as opposed to a high-level editing application such as an image editor.

Creating custom RagRE client using a DIFF patcher
-------------------------------------------------

RagRE is the abbreviation for Ragnarok Renewal client (ragexeRE.exe), which is normally updated by Gravity weekly, to add new items or features, to fix bugs and the like. This is also the client, which is currently used for rAthena. Although it is possible to use an unmodified client with rAthena (up to 2010/08/04), it is typically modified using a DIFF patcher.

Each new client requires [Shin's Diff Patcher](http://rathena.org/board/topic/53420-shins-diff-patcher/) and the [Wee Diff Gen plugin](http://rathena.org/board/topic/53421-weediffgen/2).

### Diffing your client

#### Download your client

Download a client from [here](http://subversion.assembla.com/svn/weetools/clients/). Extract the executable from the zip file, extracting requires [7zip](http://www.7-zip.org/download.html). I recommend making a folder and naming it "RagRe Exes" and in that folder create a folder with the name being your client's date. For example if my RagRe exe was "2011-04-27aRagexeRE", I would name the folder I am extracting it to "2011-04-27a", this is just to be organized and makes your exe easy to find.

#### Diffing

Download Shin's Diff Patcher and the Wee Diff Gen plugin located above. If you did not download the Plain Diff Plugin, ignore the following sentence, as WeeDiffGenerator will be the main plugin. From the drop down menu under "Select patch engine" select "WeeDiffGenerator". For "Source Executable" click "Select" and navigate to your RagRe exe's location, then select the executable. It will ask if you want it to auto-select recommended patches, click yes. Now a list of diffs will show up, with check boxes to the left. Simply decide what diff you would like to apply to your client, and click the check box. For some diffs like "Fix camera angles" you can select more than one, but its recommended that you only select one. This may change in the future. Some diffs like "Increase Headgear View ID" will have a text box pop up prompting you to enter a value. Once you are done selecting what diffs you would like to apply, make sure the "Output executable" location is alright with you, you only need to change it if you want the output executable to be saved somewhere other than the folder of the source executable's location. Click "Patch it!" and your diffed exe will now appear in either the folder where your source executable is, or where you chose to save it.

### Follow-up modifications to diffed clients

These modifications are usually applied to already DIFFed clients for finer customization, which is not possible with a DIFF by itself.

#### Custom Window Title

Requires a client, which has been patched to allow custom window title and [HxD](http://mh-nexus.de/en/hxd/), or any other hex editor.

Steps:

1.  First, you need to know what the current *window title* is.
2.  Start your client in Windowed mode to check.
3.  After closing the client, load it inside the hex editor.
4.  When the file loads, it should look something like this:
    <center>
    [Editing a ragexeRE with HxD](/Image:Hxd-main.png "wikilink")

    </center>
5.  Press **Ctrl+F** to open the Find window and input the window title. As the window title is usually stored at the beginning of the hexed client, a partial title will do.
6.  When you find the section, it will look something like this:
    <center>
    [Current Window Title](/Image:Hxd-custtitle.png "wikilink")

    </center>
7.  Now, on the **right** side (ASCII text), start where the current Window Title starts and begin overwriting it with your NEW window title.
8.  If there are leftover words after you have typed your NEW window title, switch to the **left** side (Hexadecimal) and over-write the rest of the title with 00 (zeros).
9.  Save.

#### Custom data.ini

You can rename the [DATA.INI](/DATA.INI "wikilink") file to any name that is 8 characters long (including the extension). Then, just edit your client with a Hex Editor. Find DATA.INI and replace with your new filename.

#### Custom Font

You can rename the font to any Windows Font. Just edit your client with a Hex Editor. You must find the default font and that is Arial and replace with your Font style (i.e Comic Sans Ms) **NOTE:** capital letters is incentive.

#### Custom clientinfo.xml

You can rename the [clientinfo.xml](/clientinfo.xml "wikilink") file to any name that is 15 characters long (including the extension). Then, just edit your client with a Hex Editor. Find clientinfo.xml and replace with your new filename. Note, that for newer and non-[sakray](/sakray "wikilink") clients, this file is called clientinfo.xml.

Find-Replace Hexing
-------------------

This technique is used for single features, rather than a collection of features, and is often applicable across different client versions. Such edits are distributed as a single or a set of two line edits, which specify what should be *found* and what should the found character sequence be *replaced* with, and mostly retain the length (both lines specify same amount of characters).

The character sequences are applied using a hex editor and represented by hexadecimal values of bytes, optionally each byte (two hexadecimal numbers) separated by a space. A typical find-replace hex looks like this (anti-quake patch for certain client versions[1](http://www.eathena.ws/board/index.php?showtopic=249328)):

`F: C390909090558BEC8B4508568BF1894604`
`R: C390909090C214008B4508568BF1894604`

### Application

[thumb|359px|Find and replace dialog in HxD, with a hex code ready.The](/Image:Hxd-findreplace.png "wikilink") first one is copied and pasted into hex editor find/replace window's *find* field, the latter is pasted into the *replace with* field. The search is set to be case-sensitive and then all occurrences are replaced.

The author of such **hex** may want to specify the correct amount of hits for verification. If the search does not yield any result, the hex is incompatible. The hex must **never be applied partially**, such as omitting first two bytes, as that can lead to undefined behavior.

### Variable Codes

In some instances the hex requires some variable bytes, whose value is either adjustable (replace line only) or varying among clients (both lines). This kind of *wild card* is expressed with:

-   XX - more common for adjustable values
-   ?? - is recognized as wild card in some hex editors
-   Description of the bytes in &lt; &gt;, such as 3-byte <BBGGRR> for little-endian RGB color values

Example (vending max. sell price unlocking):

`F: 3DF1B9F505`
`R: 3DXXXXXXXX`

Low-Level Hexing
----------------

Low-Level Hexing is an Ultimate Hexing Sakexe by using OllyDbg. This is Advanced technique. You need some x86 Assembly language knowledge for using this technique in order to discern the runtime order of the EXE you're looking at. The more Assembly you know, the better, as you'll be more adept at seeing what is going on.

It's necessarily quite apt to point out that in more recent times, the EXEs Gravity has put out have made things a little harder. As an example, a recent EXE, 2012-10-17bRagexeRE includes [Themida](http://anonym.to/?http://www.oreans.com/themida.php) protection, which includes anti-debugger measures. Fortunately, these anti-debugging measures aren't wholly preventative, but still provide an additional challenge; StrongOD and Phant0m allow for skipping of the anti-debug challenge, however, the other features of Themida mean that someone without experience in assembly language would be incredibly confused about the output.

### Programs needed

-   [OllyDbg](http://www.ollydbg.de/)
-   [StrongOD](http://tuts4you.com/download.php?view.2028)
-   [Phant0m](http://tuts4you.com/download.php?view.1276)

### Loading the Sakexe

Run *OLLYDBG.EXE* and select menu File &gt; Open. Then choose the Sakexe you want to Hex. If your Sakexe needs some parameters to launch (ex: 1sak1). Enter that parameter in *Arguments* field. Then press Open Button.

### Finding WinMain function

WinMain is an entry point in Windows GUI (**G**raphical **U**ser **I**nterface) applications, that is, where an application's code starts executing. This applies to the Ragnarok client as well, thus it is important to know it's location. Different compilers produce different WinMain locations.

**Note:** If you have the Windows platform SDK installed, scan the import libraries first to resolve names of a lot of common functions, such as WinMain, before hexing. This will make things easier, because you do not have to deal with plain addresses. To scan the libraries, press **Ctrl+O**, browse for the \*.lib files, and then click scan. Analyze (Ctrl+A) the client afterwards, to apply the scan results.

#### 2010-08-10aRagexeRE and older (Visual C++ 6.0)

All clients before 2010-08-18aRagexeRE (this includes all Sakexe clients) are compiled with Visual C++ 6.0 and their WinMain can be found as a CALL after the first CALL to GetModuleHandle. You can find it by a scroll down 10 - 20 lines from current position after loading Sakexe.

`PUSH    ESI`
`CALL    DWORD PTR DS:[<&KERNEL32.GetModuleHandleA>]`
`PUSH    EAX`
`CALL    Private.00694780 <--- This is WinMain call.`
`MOV     [LOCAL.24],EAX`
`PUSH    EAX`

Pressing Enter when **CALL Private.00694780** is highlighted, will make you to go to the WinMain function.

#### 2010-08-18aRagexeRE and newer (Visual C++ 9.0)

Newer clients are compiled with Visual C++ 9.0, which is part of Visual Studio 2008. The structure of the entry point is completely different and more complex than the one of the older clients. After loading the client, the position is set to a CALL which is followed by a JMP.

`CALL    Private.0074763E`
`JMP     Private.00746D24`

The CALL is not important, as it only contains compiler specific stuff. Selecting the JMP and pressing Enter will make you go the code position, where WinMain is located. Scroll down, until you find a PUSH 400000, which is an equivalent to the GetModuleHandle call in older clients. The CALL after it is the WinMain function.

`JMP     SHORT Private.00746E56`
`PUSH    0A`
`POP     EAX`
`PUSH    EAX`
`PUSH    ESI`
`PUSH    0`
`PUSH    400000`
`CALL    Private.00745790 <--- This is WinMain call.`
`MOV     DWORD PTR DS:[8AE16C],EAX`
`CMP     DWORD PTR DS:[8AE160],0`

Pressing Enter when **CALL Private.00745790** is highlighted, will make you to go to the WinMain function.

### Disable some instructions with NOP Instruction

We can disable some instruction with NOP Instruction. By Right Click on the lines you want to replace by NOP. Then, Select *Binary &gt; Fill with NOPs*. You can also replace more one line in once *Fill with NOPs*.

### Changing instruction to other instruction

We can change an instruction to other instruction by pressing *Space Bar*. With the power of *Space bar*. We can completely make modifications to our Sakexe. Such as changing *jxx* to *jmp*.

### Save our changes to Sakexe

All changes in OllyDbg is not affected on our Sakexe until we save these changes. You can *Right Click* on anywhere in CPU Window. Then select *Copy to executable &gt; All modifications*. Dialog *Copy selection to executable file* will appear. Press *Copy all* and other window will appear. Right Click on anywhere in this window and select *Save file* and *Save file as* dialog will appear. Type desired file name and press *Save* Button. You can overwrite original file. OllyDbg will automatically backup our original Sakexe if we choose overwrite original file.

See Also
--------

-   [Loading Screens](/Loading_Screens "wikilink")
-   [DATA.INI](/DATA.INI "wikilink")
-   [clientinfo.xml](/clientinfo.xml "wikilink")

External Links
--------------

-   [WeeDiffGen Plugin](http://rathena.org/board/topic/53421-weediffgen/)
-   [Shin's Diff Patcher](http://rathena.org/board/topic/53420-shins-diff-patcher/)
-   [7zip](http://www.7-zip.org/download.html)
-   [Weetools Repository](http://subversion.assembla.com/svn/weetools/)
-   [NEMO Patcher](http://rathena.org/board/files/file/3071-nemo/)

[Category:Client Configuration](/Category:Client_Configuration "wikilink")