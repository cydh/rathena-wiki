---
title: New Classes
permalink: /New_Classes/
---

This is a placeholder for the updated version of the new job classes guide. I will be back to update it once I have tested and documented the setup on the newer svns and the new wiki structure is fully implemented and layed out.

-A17kaliva

------------------------------------------------------------------------

**Note\***
Nothing Under This Header Has Been Tested As Of The Time Of Being Written! This Guide Is In Progress! Use At Own Risk!!

------------------------------------------------------------------------

Credits
-------

The new job class guide was updated and originally based off the guide written by myself (A17kaliva) which was compiled through the works and notes of various other developers noted below.

Other Contributers- Brainstorm, A17kaliva, Quanta, Omega, Terijan, Mith\*~~, Daegaladh, hondacrx & Rikter. (Several other members also helped in testing and error reporting purposes, but were omited due to space.)

Due to the rewriting of this guide, the documentation of contributions to this guide may be omitted due to new information provided, or changes in the code that render those portions unnecessary. I will however endeavor to label each contribution to this modification with the contributors name in brackets next to the sub-headers if/when possible.
A17kaliva (A-17)

------------------------------------------------------------------------

Introduction
------------

\[Original by Shizuka- Summerized by A17\]

So far, this guide is covering adding a new job as a first class (1-1) job. If you'd like more information on how the server handles the different levels of classes, take a look at doc/ea_job_system.txt in your server files. \[edit\] Preperations & Requirements

xRay Client- Can be located here \[2\]

A compiler- such as cygwin.

First things first, PLEASE BACK-UP YOUR FILES. We are not responsible for you breaking your server.

I'll be using _CUSTOM_JOB1, _CUSTOM_JOB2, etc for class variables, you CAN change this to whatever your job name is, however, it's best to follow the step by step instrunctions until your familiar with the setup.

(Note, this has no impact on the name your sprite will use ingame. Also note THIS IS CASE SENSITIVE. You must type these IN CAPS! When in doubt, please follow the structure of currently existing code.) \[edit\] Common Terms

Before reading the rest of this guide, there are some terms used you should know. Although obvious, we wish to cover all bases. -- Find : Find -- Replace : Replace the code from -- Find with this code. -- Add after : Add the necessary code after the -- Find line. -- Add before : The same as above, but this time before the line.

Part 1: Source Edits
--------------------

map/pc.h (Skill limits and jobclass id ranges.) map/atcommand.c (Settings for use of the @command @job<job#> .) map/itemdb.c (Deals with bitmasks for setting equipable items) map/map.h (Deals with the way the sprite is viewed by the client. -mapid) common/mmo.h (Settings for the jobclass \# for jobid to mapid convert.)

\[edit\] **map/pc.h** \[Shizuka\]

//PLEASE NOTE: This step is only necessary if you're going to have a class that has more than 53 skills. I increased this number because my GM class has all skills. -- Find Code:

`//Update this max as necessary. 53 is the value needed for Super Baby currently `
`#define MAX_SKILL_TREE 53`

-- Replace Code:

`//Update this max as necessary. 53 is the value needed for Super Baby currently `
`#define MAX_SKILL_TREE 600`

**//START:No need to to this in new revisions- as adding new class in mmo.h automatically increases JOB_MAX.**

//Permission to remove this chunk of code.

-- Find Code:

`//Checks if the given class value corresponds to a player class. [Skotlex] `
`#define pcdb_checkid(class_) (class_ `<JOB_XMAS>`= JOB_NOVICE_HIGH && class_ <= JOB_SOUL_LINKER)) `

-- Replace Code:

`//Checks if the given class value corresponds to a player class. [Skotlex] Revamped- [A17kaliva]`
`#define pcdb_checkid(class_) (class_ <= JOB_XMAS || (class_ >= JOB_CUSTOM_JOB1 && class_ <=`
`JOB_CUSTOM_JOB5) || (class_ >= JOB_NOVICE_HIGH && class_ <= JOB_SOUL_LINKER)) `

-   -note: on the above replacement I purposely set it so that the custom classes are a group of their own. You can extend JOB_CUSTOM_JOB5 to whatever \# of jobs you want as long as you don't skip job id \#'s. In the case of skipping id \#'s you will have to document the last job before the jump followed by:

|| (class_ &gt;= THE JOB YOU JUMPED TO && class_ &lt;= LAST JOB YOU END WITH)

**//END:No need to to this in new revisions as adding new class in mmo.h automaticaly increases JOB_MAX.**

\[edit\] map/atcommand.c \[Fixed: A17kaliva\]

-- Find Code:

`        { "ninja",   25 }, `

-- Add after Code:

`        { "custom job1",   4053}, `
`        { "custom job2",   4054 }, `
`        { "custom job3",   4055 }, `
`        { "custom job4",   4056 }, `
`        { "custom job5",   4057 }, `

\[edit\] common/mmo.h \[Fixed: A17kaliva\]

`   * (note: Seems you can use anything over 4053 safely... however these are tested and work.)`

-- Find Code:

`  JOB_XMAS, `

-- Add after Code:

`  JOB_CUSTOM_JOB1 = 4053, `
`  JOB_CUSTOM_JOB2, `
`  JOB_CUSTOM_JOB3, `
`  JOB_CUSTOM_JOB4, `
`  JOB_CUSTOM_JOB5, `

**//START:No need to to this in new revisions- as adding new class in mmo.h automatically increases JOB_MAX.**

//Permission to remove this chunk of code.

\[edit\] **map/map.h**

The check that caps the ID at 4050:\[Mith\*~~\] -- Find

1.  define MAX_PC_CLASS 4050

-- Replace

1.  define MAX_PC_CLASS 4500

(note: Its not required to go this high, I did it for space/testing reasons. Set it to the range of jobs you add.)

(It appears that this no longer needs to be edited; there's new code that seems to automatically calculate the number of IDs needed, and there's no 'cap' anymore. At least, I can't find it in my revision. \[Reborn\])

**//END:No need to to this in new revisions- as adding new class in mmo.h automatically increases JOB_MAX.**

-- Find Code:

`  MAPID_XMAS, // [Valaris] `

-- Add after \[Fixed: A17kaliva\] (\*SEE NOTES IN BITMASKING SECTION HERE: \[3\] ) Code:

`  MAPID_CUSTOM_JOB1 = JOBL_2|0x01, `
`  MAPID_CUSTOM_JOB2, `
`  MAPID_CUSTOM_JOB3, `
`  MAPID_CUSTOM_JOB4, `
`  MAPID_CUSTOM_JOB5, `

\[edit\] map/pc.c \[Shizuka\]

-- Find Code:

`     case JOB_XMAS: `
`        class_ = MAPID_XMAS; `
`        break; `

-- Add after Code:

`     case JOB_CUSTOM_JOB1: `
`        class_ = MAPID_CUSTOM_JOB1; `
`        break; `
`     case JOB_CUSTOM_JOB2: `
`        class_ = MAPID_CUSTOM_JOB2; `
`        break; `
`     case JOB_CUSTOM_JOB3: `
`        class_ = MAPID_CUSTOM_JOB3; `
`        break; `
`     case JOB_CUSTOM_JOB4: `
`        class_ = MAPID_CUSTOM_JOB4; `
`        break; `
`     case JOB_CUSTOM_JOB5: `
`        class_ = MAPID_CUSTOM_JOB5; `
`        break; `

-- Find Code:

`     case MAPID_BABY_ROGUE: `
`        return JOB_BABY_ROGUE; `

-- Add after Code:

`     case MAPID_CUSTOM_JOB1: `
`        return JOB_CUSTOM_JOB1; `
`     case MAPID_CUSTOM_JOB2: `
`        return JOB_CUSTOM_JOB2; `
`     case MAPID_CUSTOM_JOB3: `
`        return JOB_CUSTOM_JOB3; `
`     case MAPID_CUSTOM_JOB4: `
`        return JOB_CUSTOM_JOB4; `
`     case MAPID_CUSTOM_JOB5: `
`        return JOB_CUSTOM_JOB5; `

-- Find Code:

`  default: `
`     return msg_txt(650); `

-- Add before Code:

`  case JOB_CUSTOM_JOB1: `
`     return msg_txt(1000); `
`  case JOB_CUSTOM_JOB2: `
`     return msg_txt(1001); `
`  case JOB_CUSTOM_JOB3: `
`     return msg_txt(1002); `
`  case JOB_CUSTOM_JOB4: `
`     return msg_txt(1003); `
`  case JOB_CUSTOM_JOB5: `
`     return msg_txt(1004); `

\[edit\]

Part 2: Database Edits
----------------------

`conf/import/msg_conf.txt (Deals with how messages are delivered to the jobclasses)`
`db/const.txt (Deals with source to script settings for bitmasks and id #'s.)`
`db/skill_tree.txt (Deals with how skills are governed to new classes)`
`db/exp.txt & db/exp2.txt (Experence tables - base and job)`
`db/job_db1.txt (Sets defines on jobclass -Weight,HPFactor,SPFactor.)`
`db/job_db2.txt (Sets defines on Job-specific Stat Bonuses.)`

// --- db/const.txt \[Fixed: A17kaliva\] -- Find Code:

`Job_Xmas   26 `

-- Add after Code:

`Job_Custom_Job1   4053 `
`Job_Custom_Job2   4054 `
`Job_Custom_Job3   4055 `
`Job_Custom_Job4   4056 `
`Job_Custom_Job5   4057`

I've left room here for the possibility of the 3 rumored new jobs here. If you don't know what's going on here, google hex numbers. In short, (Hexing--- 01-09=1-9, A=10, B=11, C=12, D=13, E=14, F=15, 10=16, 11=17) (\*SEE NOTES IN BITMASKING SECTION HERE: \[4\] )

-- Find Code:

`EAJ_NINJA   0x0A `

-- Add after Code:

`EAJ_CUSTOM_JOB1    JOBL_2|0x1  `
`EAJ_CUSTOM_JOB2    JOBL_2|0x2  `
`EAJ_CUSTOM_JOB3    JOBL_2|0x3  `
`EAJ_CUSTOM_JOB4    JOBL_2|0x4  `
`EAJ_CUSTOM_JOB5    JOBL_2|0x5  `

// --- conf/import/msg_conf.txt -- Add Code:

`1000: Custom Job1 `
`1001: Custom Job2 `
`1002: Custom Job3 `
`1003: Custom Job4 `
`1004: Custom Job5`

// --- db/skill_tree.txt Here you have to add one line to each skill of the custom class. The structure is simple, put the class ID,SkillID,MaxLv, and after put the PrerequisiteID,PrerequisiteLV for each prerequisite skill. -- Add Code:

`4053,1,9,0,0,0,0,0,0,0,0,0,0 //NV_BASIC#Basic Skill# `

This adds the Novice's Basic Skill (MaxLv 9) in the Custom_Job1 Skill Tree. Make sure to insert the Novice's Basic Skills and Call Baby.

// --- db/exp.txt & db/exp2.txt Inside this file there are many Base and Job Exp tables. Each table starts with the MaxLv and the IDs of the classes that will use it, seperated by ":". Just insert the ID of your custom there. -- Find Code:

`50,1:2:3:4:5:6:26:4024:4025:4026:4027:4028:4029:4046 `

-- Add after Code:

`50,1:2:3:4:5:6:26:4024:4025:4026:4027:4028:4029:4046:4053 `

Now Custom_Job1 uses the Job Exp Table of 1st Classes.

// --- db/job_db1.txt This file defines the values of each class, Weight, HP multiplicator and bonus with weapons. Copy someone's values and modify them.

// --- db/job_db2.txt Here you define the Stat Bonus. First put your custom ID, and after add one field for each JobLvUp that your class has. Novice has MaxJobLv 10 so it has 9 fields (Lv2,Lv3,Lv4...). In each field put the number of the stat that you want to be increased by 1. -- Legend Code:

`0 = No stat bonus at this job level `
`1 = STR increased by 1 at this job level `
`2 = AGI increased by 1 at this job level `
`3 = VIT increased by 1 at this job level `
`4 = INT increased by 1 at this job level `
`5 = DEX increased by 1 at this job level `
`6 = LUK increased by 1 at this job level  `

Now that the hard part is over... Let's work on the client stuff!

\[edit\]

Part 3: Client Files
--------------------

`class_tab.txt (Deals with how the classes are loaded.)`
`imf_tab.txt (? Deals with the default hair & act location it seems)`
`monstrosity_tab.txt (The visable name of the sprite. -Jobname)`
`reality_dir_tab.txt (tells client which folder to look for the job's weapon sprite/act files)`
`reality_tab.txt (? I'm guessing class to equip relation.)`

You'll have to add class sprites & weapon sprites for each class (easy if you're using class sprites based on original sprites or just copy and pasting the original sprites), and, of course, edit the _tab files.

Before we edit the tabs, we need to add some files to the data folder. Create the following folders if you don't have them in your data folder already: Code:

`data\sprite\ÀÎ°£Á·          // Item Sprite folder`
`data\sprite\ÀÎ°£Á·\¸öÅë     // Jobsprite folder`
`data\imf                    // .Imf folder`

// --- data\\sprite\\ÀÎ°£Á· Create a NEW folder for each class named the same as the class. Inside these folders will be the weapon sprites for each respective class.

For this example, the following folders would be created: Code:

`custom_job1 `
`custom_job2 `
`custom_job3 `
`custom_job4 `
`custom_job5 `

// --- data\\sprite\\ÀÎ°£Á·\\¸öÅë Inside this folder create two folders, ³² for male sprites and ¿© for female sprites. Add .spr and .act files for each of your new classes, inside these folders, with prefix ³² for male and ¿© for female. Code: -Inside ³² folder:

`custom_job1_³².spr and custom_job1_³².act `
`custom_job2_³².spr and custom_job2_³².act `
`custom_job3_³².spr and custom_job3_³².act `
`custom_job4_³².spr and custom_job4_³².act `
`custom_job5_³².spr and custom_job5_³².act `

-Inside ¿© folder:

`custom_job1_¿©.spr and custom_job1_¿©.act `
`custom_job2_¿©.spr and custom_job2_¿©.act `
`custom_job3_¿©.spr and custom_job3_¿©.act `
`custom_job4_¿©.spr and custom_job4_¿©.act `
`custom_job5_¿©.spr and custom_job5_¿©.act `

// --- data\\imf \[Thank Omega for the .imf clarification\] .imf -- It's still unclear what this file does, but the client requires it for all classes.

It's noted that it has something to do with the default head/hairstyle for each class and may effect the starting placement of the act file.

You can find the english names for each sprite name here \[5\], thanks goes out to the guys at Rate My Server.

If you're using sprites made from any of the default classes, I suggest you use the same .imf file. For example, if you have sprite made from the original Dancer sprite, use the .imf for dancer.

You have to use sex prefix for the .imf files, _³² for male, and _¿© for female.

// --- class_tab.txt Ok A heads up CLASS_TAB, REALITY_TAB, and REALITY_DIR_TAB all run differently than the monstrosity tab. Actually I dare you to go in there and actually find where its even once mentions a 2-1 2-2 or trans class sprite.

IT doesn't... Instead it refers to them differently. Now you don't have to add !\#\#\# here.

At the end of the file -- Find

-   ÃÊº¸ÀÚ

-- Add BEFORE Code:

`custom_job1 `
`custom_job2 `
`custom_job3 `
`custom_job4 `
`custom_job5 `

-   Do the same for reality_tab.txt and imf_tab.txt. (&lt;--BOLDED! your sure to miss this step if I don't.)

// --- reality_dir_tab.txt -- Find

-   ÃÊº¸ÀÚ\\\\ÃÊº¸ÀÚ

-- Add BEFORE Code:

`custom_job1\\custom_job1 `
`custom_job2\\custom_job2 `
`custom_job3\\custom_job3 `
`custom_job4\\custom_job4 `
`custom_job5\\custom_job5 `

// --- monstrosity_tab.txt Add your class ids in order. For my ID 4053, I'll add my classes after the !4053 line.

Remember that the monstrosity_tab uses proper caps and spaces for class names (how they will appear in the client. This is where you will name your class according to what it will be AKA. Bard, Etc.) -- Find Code:

!4001

-- Add after Code:

`!4053 `
`Custom Job1 `
`Custom Job2 `
`Custom Job3 `
`Custom Job4 `
`Custom Job5`

\[edit\]

Bitmasking
----------

\[A17kaliva & Rikter\]

**Description:** This Section deals with equipped items and how they are displayed and be equipped on your custom classes.

Ok, Now we get dirty... First thing you should know is that the bitmasks are limited to 32 for the jobclass equipments. You also need to understand that 0 is also counted so the max is 31.\[Brainstorm\]

That being said, we shall start.

Earlier we set up the job ids to run on specific map ids, your map ids are set by bitmasks in map.h and also in itemdb.c which we haven't referred to yet for a reason.

When you set up your bit masks you will notice this:

`   MAPID_NOVICE = 0x0,`

This is followed by the other base 1-1 classes starting with swordsman at 0x1 through thief at 0x6. These are the preliminary base hex that defines all items that can be equipped.

\[Mith\*~~\] If my job's "bitmask number" is 24, then I do 2^24, which results in "16777216".

I then take that big number over there and convert it to hexadecimal, using any converter, like this one \[7\] , and the result is "1000000"... I then add a prefix "0x" for all bitmasks, and there you go, my job's bitmask is "0x1000000".

When you set up an item in your item DB you will need to add this item to the place marked job. Example this is a monk weapon:

1522,Stunner,Stunner,4,60000,,2000,140,,1,0,0x00008110,7,2,2,3,27,1,8,{ bonus2 bAddEff,Eff_Stun,1000; },{},{}

\[A17kaliva\] However, what Mith didnt know is that while he was right about the itemdb.c defining the bitmask for a job, the main define wasn't held there.

The itemdb.c as referred to by brainstorm at the time I was trying to crack my system to allow new jobclasses without a hex edit "The itemdb.c defines how the upperclass characters receive the ability to equip items from their lower class counterparts."

In other words, this (below) refers to which items the upper class will be able to equip.

`   if (jobmask & 1<<JOB_MONK)`
`       bclass[2] |= 1<<MAPID_ACOLYTE;`

This bit of code here is calling for the hex (0x______ ) that you placed in the map.h, it refers to monk as bclass 2 and that it inherits the abilities from it's base job.

Why is that needed? Well, it's NOT needed unless you are going to make trans classes.

Remember how Brainstorm said the hex was limited to 32? If you haven't noticed, gravity has more than 32 classes.

Now, if the limit is 32 how is it that we are able to use around 36? Well the key is in the base classes and the itemdb.c ... The base hex is the same thing you're using at the moment, and will be your key to how things get equipped to your new classes.

I noticed a few extra bits of coding in the source that, well for all intents and purposes did basically nothing. It was a \# define that defined a variable that wasn't being used.

Pay attention to what I'm showing you this will be the key to showing your items.

In your map.h:

`//These marks the "level" of the job.`
`#define JOBL_2_1 0x100 //256`
`#define JOBL_2_2 0x200 //512`
`#define JOBL_2 0x300`
`#define JOBL_UPPER 0x1000 //4096`
`#define JOBL_BABY 0x2000  //8192`

Now search your ENTIRE map.h for JOBL_2 ... It doesn't exist! This entire define was pointless and I had a feeling it was set up in the past for possible new classes.

If you scroll down further in your map.h you will locate this:

`//2_1 classes`
`   MAPID_SUPER_NOVICE = JOBL_2_1|0x0,`
`   MAPID_KNIGHT,`

now remember the define we had above?

`JOBL_2_1 = 0x100`

So Super Novice equipment id is 0x0 + 0x100 or 0x100. Simple huh? Well lets check it, to do that we take the id 2^0 = 0 then 0 in hex is 0 + define 100= 100.

Now try it for knight. . . Knight is 0x1 + 0x100 = 0x101 (1^1= 1 + define 100 = 101.) (some of you are going WTF. . . Were dealing with hex not normal numbers. 0x01 is the same as 0x001 = 0x00000000000000000001 ... )

Now look at the LK. Note his bitmask:

`   MAPID_LORD_KNIGHT = JOBL_UPPER|JOBL_2_1|0x1,`

so for the LK his \#s are \[(upper=1000)+ (job2_1=100)+(0x1=1)\]=1101...

Now if you wanted all the swordie classes to use this item, you would have to add all the \#'s of each jobclass that uses it.

What I did to make yours run, is set the define to run as 300. So, what your system is going to do, is add both 100 and 200 together. This means your bitmask for your new job will be found by what I had you set in the map.h ...

So your new class

`   MAPID_CUSTOM_JOB1 = JOBL_2|0x1,     // Uses same weapons as swordman classes  -- `
`   MAPID_CUSTOM_JOB2 = JOBL_2|0x2,     //uses same as mage-`
`   MAPID_CUSTOM_JOB3 = JOBL_2|0x3,     //archer-`
`   MAPID_CUSTOM_JOB4 = JOBL_2|0x4,     //acolyte-`
`   MAPID_CUSTOM_JOB5 = JOBL_2|0x5,     //merchant-`

(understand now? simple no?) WAIT! It's not over... The way it runs now, this new class can equip any swordsman based items, in other words to get it to run it has to be identical to having the bitmask set as job1-1 job2-1 and job2-2's bitmasks, meaning you have to add all 3 up.

You cannot make it not able to equip the other classes items since those run on it. This also means that it's other classes will be able in theory to use these new items also. If you were to add the upper as in the instance of the LK it would be = to all of the swordsman class IDs.

To fix this, we can add a new define in the source like this:

`#define JOBL_3 0x400 `

This should make it only able to use the previous class weapons, meaning if you used JOBL_3|0x4, It would only be able to use the acolyte or the 1-1 class weapons. You would also have to figure out what the new id would be as it would be higher.

I haven't tested what happens if you add the upper to JOBL_3|0x4, (making it JOBL_UPPER|JOBL_3|0x4,) but I have a feeling it would allow you to only equip the 1-1class, 2-1, and 2-2 classes weapons and not the trans classes. (big thanks to Rikter for testing it out and giving me feedback on how it ran.)

(NOTE: Without adding a new define of 400, or the upper you are only able to add 1 custom class per original bitmask. In other words you can only make one swordsman type unless you add the upper. If you do add the upper then it will allow for 2. By adding a new define of 400 you can add 3 and with upper, and 400, 4.)

Enjoy. \[edit\] Tables

See this post for a better understanding of the tables.

\[8\]\[Daegaladh\] \[edit\] Things things to be added eventually

\[edit\]--[Rad417](/User:Rad417 "wikilink") 07:47, 25 December 2009 (UTC)

Added code boxes instead of just a block of text for easy reading.

Noted some parts that needs to be removed as they are not needed anymore.

Corrected grammar, punctuation marks and spacing in some parts

Note: anyone can ammend this guide if they choose too as long as credit is given back to the prior contributors, So if you haveanything to add that will benifit the community feel free to add it here. Adding classes to exp.txt, exp2.txt, skill_tree.txt, job_db1.txt and job_db2.txt, & Adding Male and female sprite files.

[Category:Client Configuration](/Category:Client_Configuration "wikilink") [Category:Configuration](/Category:Configuration "wikilink") [Category:Source Snippets](/Category:Source_Snippets "wikilink")