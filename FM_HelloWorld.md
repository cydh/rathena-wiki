---
title: FM HelloWorld
permalink: /FM_HelloWorld/
---

<div style="clear: both;">
</div>
<div style="background:#400; color: #fff; padding-left: 3px;">
These FM (Follow Me) Tutorials are a collaboration of NPC's that are meant to teach you how to effectively use commands in the Athena Scripting Language and to help you better yourself as an rAthena Scripter.

All Tutorials found on here regarding FM Tutorials are based on the following conditions:

-   It's assumed that you are working under the NPC Directory (This is stated below)
-   It's assumed that you are using and naming the files in the same convention as the tutorial
-   It's assumed that your root rathena folder is called /rathena/

</div>
<div style="background:#004; color: #fff; padding-left: 3px; float: right;">
This Tutorial **FM_HelloWorld** will help you understand the following:

-   Using a Custom Configuration File
-   Main NPC Structure
-   Commands
    -   mes
    -   close
-   Loading a NPC File
-   Previewing the NPC on the Server

</div>
<div id="Introduction">
</div>
Introduction
============

<div id="Introduction-WhatNPC">
</div>
What is a NPC?
--------------


NPC's (Also Known as **N**on-**P**layable **C**haracters) are found in EVERY game you have every played in your entire life. Whether it's a shop that you buy items at, a random person walking around in town, or a person that has a quest for you. Any character you see or possibly don't see, that can interact with the player that is not controlled by another player is a NPC.

<div id="Introduction=WhatScripting">
</div>
What is NPC Scripting?
----------------------


NPC Scripting is a psuedo-language built around the C Source Code from the rAthena Emulator. This langauge allows us to directly create NPC's that can interact with the Server Community.

<div id="Introduction-WhyHere">
</div>
Why are YOU Here?
-----------------


NPC Scripting can be as complicated as you want to make it. Fortunately, you have to start somewhere, and that somewhere, is right here!

<!-- -->


Every NPC Scripter has gone through some kind of tutorial, learned from some kind of script, and that's exactly what we are going to focus on today. Following this guide will teach you step by step instructions on creating and maintaining your own set of unique and customizable NPC's!

<div id="Comments">
</div>
Comments
========


Comments are basically bits of information that you want to store in the file, but not necessarily be read by the server. In order to add a comment, whether it's to a config file (as we are about to do) or a NPC Script File, simply please // in front of ANY text on a line...

-   Example: // This is Commented Out (Not Read By Server)

<div id="LocatingNPCFolder">
</div>
Locating the NPC Folder
=======================


First, you must locate your root installation. Normally this could be something like 'c:\\rAthena\\' or maybe your desktop at 'c:\\documents and settings\\<your_name>\\desktop\\rAthena\\' or 'c:\\users\\<your_name>\\desktop\\rAthena\\' no matter where the location, simply find this directory. Inside, you will find a folder called /npc/ ... Here, all NPC Files are located.

<div id="CreatingCustomNPCFolder">
</div>
Creating Your Own Custom Folder
===============================


Whenever you script, it is nice to have all your custom scripts belonging to you in a special place. For this, we will create the directory that will be used for all FM Tutorials. Simply navigation to your /NPC/ folder, and create a new folder called /FM_Tutorials/

<div id="CustomConfig-Create">
</div>
Creating Custom Configuration File
==================================

<div id="CustomConfig-What">
</div>
What is a Configuration File?
-----------------------------


You may notice a few **\*.conf** files at the bottom. These are configuration files... There is ONE file in particular that you will need to focus on for this tutorial session. This file is called **scripts_main.conf**. This file, controls and imports all other \*.conf files and uses them to house collections of npc's in segregated areas.

<div id="CustomConfig-How">
</div>
How To?
-------


Open Notepad, or your editor of choice, I'm currently using Notepad++ and Sublime 2, however this is all relative and unique to the individual. Create a blank file (because we don't know what exactly we will be importing just yet) and Save in the in the NPC folder as **FM_Tutorials.conf**.

<div id="CustomConfig-WhyImportant">
</div>
Why is This Important ?
=======================


The reason we use our custom configuration file is simple. In the event of a new rAthena Release, files copied over, will generally overwrite the ones that came natively with rAthena. This includes the file **scripts_main.conf** and all OTHER **\*.conf** files you see there. The reason we create our own, is because on an update, our file will NOT be overwritten, and thus the only thing we have to do to restore it, is to simply add the import line back into the file **scripts_main.conf**.

<div id="ImportCustomConfig-What">
</div>
Importing Custom Configuration File
===================================

<div id="ImportCustomConfig-How">
</div>
How To?
-------


Now that we have our custom configuration file **FM_Tutorials.conf**. We can now look at the line for import to place into **scripts_main.conf**.

<!-- -->


Notice! The line that we place in **scripts_main.conf** is the ONLY line we may have to re-add in the event of a SVN Update that may or may not modify this file!

<!-- -->


You may notice some other lines in this file that look similar to each other... These are the **import** tags. Anywhere near the bottom of the page add the following line:

-   import: /npc/FM_Tutorials.conf

<div id="HelloWorld-NPC">
</div>
Creating Our First FM_HelloWorld NPC
=====================================


We are now ready to begin creating our first npc! Again, you can use whatever editor you feel most comfortable in! All Examples will be in Plain Text.

<div id="HelloWorld-MainStructure">
</div>
Main NPC Structure
------------------


The **Main NPC Structure** looks like the following:

<!-- -->

    prontera,158,173,4  script  FM_HelloWorld   47,{

    }

Let's now break down each component of the NPC Header (Please note, the spacing between the sections are TABS, NOT SPACES, and will be referenced with a {TAB} marker.

Notice, these sections are separated by TABS and NOT SPACES (Here is the same text using our {TAB} example.

    prontera,158,173,4{TAB}script{TAB}FM_HelloWorld{TAB}47,{

    }

<div id="HelloWorld-MainStructure-Map">
</div>
### Map


To put it simply, this is the mapname that the NPC will be placed on. In earlier versions of rAthena it was required to put the \*.gat extension on these maps, however, this has been changed and you can now simply use the mapname without the extension. (However, if you are unsure about the extension feature, you can STILL use the .gat extension the map name). A List of available server maps can be found in the following location.

-   /rathena/conf/maps_athena.conf

This file contains all the loaded maps. Please Keep in Mind // in front of ANY line means this is commented out and does not get read from the server.

<div id="HelloWorld-MainStructure-XY">
</div>
### X,Y


These are the coordinates that the NPC will be located at. This can be hard to determine since you do not have any active way of determining "Where you are" in the world of Ragnarok. However, there is a small trick you can do to figure out where you should place your NPC.

<!-- -->


Login to your server and walk around... Stand exactly where you would like your NPC to stand, and type in the following command:

-   **/where**


This will message you the x and y coordinates that you can use to place your npc file exactly where you want it displayed.

<div id="HelloWorld-MainStructure-Direction">
</div>
### Direction


Direction can be tricky to understand. In simple terms, there are 8 different location points... Depending on which way you want the NPC to face.

<!-- -->

    [1][8][7]
    [2][0][6]
    [3][4][5]


My suggestion, is to fiddle with the values 1-8 until you determine which one you like the most.

<div id="HelloWorld-ScriptType">
</div>
### Script Type


There are two types of scripts you can create in the Athena Scripting Language. These types are:

shop
A shop script is a simple buy / sell npc that allows you to place items into it, at specific buy and sell prices. This will be covered in a later tutorial.

script
This is exactly what we are doing right now. a script NPC is one that utilizes command functions to interact with a player and perform different tasks based on numerous checks.

<div id="HelloWorld-NPCName">
</div>
### NPC Name


This is the display that you see when you look at the NPC in-game. This display name can be pretty long, up to about 24 characters I believe, and can include spaces.

<div id="HelloWorld-NPCID">
</div>
### NPC ID


The NPC ID, is a Unique Identifier to the Sprite File for the NPC's. A suitable list can be found at this URL: <http://nn.nachtwolke.com/dev/npclist/> , however there are many sits that allow you to view NPC ID's.

<!-- -->


For the sake of ease, all npc's created by the AS Tutorials, will use the Sprite ID 47.

-   <http://i.imgur.com/HEDvF.gif>

<div id="HelloWorld-OpenCloseBrackets">
</div>
### Open and Close Brackets


The Brackets { and } you will see many times, along with the command ( )... It is important to note, that every beginning has an end.

<!-- -->


The Main NPC Structure utilizes these brackets { } and anything that the npc says, does, or doesn't do, will be located inside.

<div id="FirstCommands">
</div>
Our First Commands
------------------


In this tutorial, we will be covering Two (2) of the most basic commands of NPC Scripting. These two commands are found below.

<div id="FirstCommands-MES">
</div>
### 'mes' Command


The [mes](/Mes "wikilink") statement simply allows us to tell the NPC what to display in the dialog box.

<!-- -->


Let's go ahead and add a mes line to our NPC in order him to say the phrase "Hello World"

<!-- -->


Within the **NPC's Main Structure** we will place the following code

<!-- -->

    mes "Hello World";


There are a few things to notice about this command:

-   The command is all lowercase (script commands and variable names are NOT case-sensitive. 'mes' is the same as 'Mes' which is the same as 'MES')
-   We wrap the string in " " and not ' '
-   We end EVERY command line with a semi-colon ;


If you have done the following correctly your current npc script should now look like:

<!-- -->

    prontera,158,173,4  script  FM_HelloWorld   47,{
        mes "Hello World";
    }

However, we cannot end just there. If we do not include a special close argument, this will freeze on the users screen, because they have no way of getting this dialog box to close.

<div id="FirstCommands-CLOSE">
</div>
### 'close' Command


The close command, simply allows the users to close the dialog box at specific times (whenever it's read in the file)

<!-- -->


In order for us to use this command, we would have to have first shown something in the dialog box.

:; Have we already done this? Yes! We called the [mes](/Mes "wikilink") command which opened a dialog box!



Now let's simply add the following line after the [mes](/Mes "wikilink") command.

<!-- -->

    close;


This will tell the script that we are done showing messages to the user for now, would like the user to stop talking to the npc, and offer the close option.

<!-- -->


Once again, if all went according to plan, your NPC should contain the following code:

<!-- -->

    prontera,158,173,4  script  FM_HelloWorld   47,{
        mes "Hello World";
        close;
    }

<div style="background:#400; color:#fff; padding-left:3px;">
This concludes the scripting portion of this tutorial. Please save your work as the following:

-   /npc/FM_Tutorials/FM_HelloWorld.txt

</div>
<div id="AddToConfig">
</div>
Adding Our FM_HelloWorld NPC to Configuration File
===================================================


Adding a script to our configuration file tells the server that we want to include this script when it builds the npc's to load into the server.

<div id="AddToConfig-How">
</div>
How To?
-------


Open your Custom Configuration File: **FM_Tutorials.conf**

<!-- -->


This configuration file is currently blank. We are going to add two lines to this file.

-   The first, will be a comment that states "FM_HelloWorld Tutorial NPC"
-   The second, will be a command to add the npc to the file.

<!-- -->

    // FM_HelloWorld Tutorial NPC
    npc: npc/FM_Tutorials/FM_HelloWorld.txt


A few things to note:

-   // FM_HelloWorld Tutorial NPC
    -   Previously found under [Comments](/Scripting_Tutorials:FM_HelloWorld#Comments "wikilink") we know that the server will ignore this text, allowing us to place it here and keep notes to ourselves.
-   npc:
    -   This tells the configuration file that we want to load this NPC
-   npc/FM_Tutorials/FM_HelloWorld.txt
    -   This is the path of the file, relative to the root folder... example /rathena/npc/FM_Tutorials/FM_Helloworld.txt is the same thing, however we are basing this on the root folder as if we were already there.

<div id="Testing">
</div>
Testing Our FM_HelloWorld NPC
==============================


Congradulations! You have successfully finished your first tutorial on NPC Scripting!

<div id="Testing"-How>
</div>
How To?
-------


In order to test to see if your NPC now loads, simply run your server and login. Move your character to the location where you wanted to place the npc and you should now see him in your server and he will speak to you if you click it!

[Category:Scripting_Tutorials](/Category:Scripting_Tutorials "wikilink") [Category:FM_Tutorials](/Category:FM_Tutorials "wikilink")