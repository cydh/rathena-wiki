---
title: Custom Jobs
permalink: /Custom_Jobs/
---

\[Guide\] Add Custom Job

By: **Ratalaika**

On this page, you will be able to learn the steps on how to add your Custom Job. First off:

**1.** Open the file

Search for the lines:

`   JOB_SUMMER,`
`   JOB_MAX_BASIC,`

Then replace it with:

`   JOB_SUMMER,`
`   JOB_BURGLAR= 35,`
`   JOB_MAX_BASIC,`

Save the file.

Next, open

Search for the lines:

`           { "ninja",    25 },`
`           { "high novice",    4001 },`

Then replace it with:

`           { "ninja",    25 },`
`           { "burglar",    35 },`
`           { "high novice",    4001 },`

Save the file and open

Search for the lines:

`   MAPID_NINJA,`
`   MAPID_XMAS,`
`   MAPID_SUMMER,`

Then replace it with:

`   MAPID_NINJA,`
`   MAPID_XMAS,`
`   MAPID_SUMMER,`
`   MAPID_BURGLAR = 0x0E,`

Save the file and open

Search for the lines:

`   if (jobmask & 1<<JOB_NINJA)`
`       bclass[0] |= 1<<MAPID_NINJA;`
`}`

Then replace it with:

`   if (jobmask & 1<<JOB_NINJA)`
`       bclass[0] |= 1<<MAPID_NINJA;`
`   //items job`
`   if (jobmask & 1<<35)`
`       bclass[0] |= 1<<MAPID_BURGLAR;`
`}`

Save the file and open

Search for the lines:

`       case JOB_SUMMER:`
`           class_ = MAPID_SUMMER;`
`           break;`
`       default:`
`           return -1;`
`   }`
`   return class_;`
`}`

Then replace it with:

`       case JOB_SUMMER:`
`           class_ = MAPID_SUMMER;`
`           break;`
`       case JOB_BURGLAR:`
`           class_ |= MAPID_BURGLAR;`
`           break;`
`       default:`
`           return -1;`
`   }`
`   return class_;`
`}`

Search for the lines:

`       case MAPID_SUMMER:          return JOB_SUMMER;`

Replace it with:

`       case MAPID_BURGLAR:            return JOB_BURGLAR;`

Finally search for the lines:

`   case JOB_SUMMER:`
`       return msg_txt(621);`

And replace it with:

`   case JOB_BURGLAR:`
`       return msg_txt(700);`

Now you have finally modified the src files, once that is done recompile it.

**2.** Now we need to edit the **db** files, in order to do that, find the **db** folder. Once the folder is opened, look for and open it.

Once done, look for the lines:

`Job_Gunslinger    24`
`Job_Ninja    25`
`Job_Xmas    26`

Then replace it with:

`Job_Gunslinger    24`
`Job_Ninja    25`
`Job_Xmas    26`
`Job_Burglar    35`

Now after that, find the lines that are shown below (The lines are still under **const.txt**):

`EAJ_TAEKWON    0x7`
`EAJ_GUNSLINGER    0x9`
`EAJ_NINJA    0x0A`

Then replace it with:

`EAJ_TAEKWON    0x7`
`EAJ_GUNSLINGER    0x9`
`EAJ_NINJA    0x0A`
`EAJ_BURGLAR    0x0E`

Once you have finished editing those lines, save it then close.

Now, you will have to look for the txt file named **exp.txt**.

`Maximum Level Syntax line: `**`0:1:2:3:4:5:6:7:8:9:10:11:12...`**

Then replace it with:

`Maximum Level Syntax line: `**`0:1:2:3:4:5:6:7:8:9:10:11:12:35...`**

In the same file we look for:

`your max level,1:2:3:4:5:6:26:4046,1`

We need to change to code like this:

`your max level,1:2:3:4:5:6:26:4046:35,1`

We need to edit job_db1.txt And at the end of everything we need to paste this:

`//Burglar`
`35,    28000,70   ,500  ,200  ,400  ,500  ,550  ,600  ,650  ,700  ,700  ,750  ,650  ,700  ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000`

This line is the one of the swordman but you can copy any other just changing the first number which is the jobid or if you prefer you can make your own.

Edit the file job_db2.txt At the end:

`//Burglar`
`35,0,1,0,0,0,3,0,0,0,5,0,0,0,1,0,0,0,3,0,0,0,5,0,0,0,6,0,0,0,2,0,0,1,0,0,5,0,3,0`

1,0,3,0,6,0,2,1,0,1,1

This line is the Swordsman you can copy any classes job id (first number) or you can make your own

Now it's time to add this skill to skill_tree.txt At the end of everything we put this

`//Burglar`
`//REQUIRED`
`35,1,9,0,0,0,0,0,0,0,0,0,0 //NV_BASIC#Basic Skill#`
`35,142,1,0,0,0,0,0,0,0,0,0,0 //NV_FIRSTAID#First Aid#`
`//What ever skills you want you can add`
`35,2,10,0,0,0,0,0,0,0,0,0,0 //SM_SWORD#Sword Mastery#`
`35,4,10,0,0,0,0,0,0,0,0,0,0 //SM_RECOVERY#Increase HP Recovery#`
`35,5,10,0,0,0,0,0,0,0,0,0,0 //SM_BASH#Bash#`
`35,6,10,0,0,0,0,0,0,0,0,0,0 //SM_PROVOKE#Provoke#`
`35,7,10,5,5,0,0,0,0,0,0,0,0 //SM_MAGNUM#Magnum Break#`
`35,8,10,6,5,0,0,0,0,0,0,0,0 //SM_ENDURE#Endure#`
`35,26,2,24,1,0,0,0,0,0,0,0,0 //AL_TELEPORT#Teleport#`
`35,27,4,26,2,0,0,0,0,0,0,0,0 //AL_WARP#Warp Portal#`
`35,28,10,0,0,0,0,0,0,0,0,0,0 //AL_HEAL#Heal#`
`35,33,10,22,3,0,0,0,0,0,0,0,0 //AL_ANGELUS#Angelus#`
`35,34,10,22,5,0,0,0,0,0,0,0,0 //AL_BLESSING#Blessing#`
`35,35,1,28,2,0,0,0,0,0,0,0,0 //AL_CURE#Cure#`
`//REQUIRED`
`35,410,1,0,0,0,0,0,0,0,0,0,0 //WE_CALLBABY#Call Baby#`
`35,681,1,0,0,0,0,0,0,0,0,0,0 //ALL_INCCARRY#Enlarge Weight Limit R#`

And that's the skill that will take the Job you want to put your job of copying the line you want such as:

`//Double Attack Skill`
`12,48,10,0,0,0,0,0,0,0,0,0,0 //TF_DOUBLE#Double Attack#`

And so it is our job so we would have to modify

`35,48,10,0,0,0,0,0,0,0,0,0,0 //TF_DOUBLE#Double Attack#`

We changed the first number to get the id of our job if you design your own set of skills you can't forget to put these:

`35,1,9,0,0,0,0,0,0,0,0,0,0 //NV_BASIC#Basic Skill#`
`35,142,1,0,0,0,0,0,0,0,0,0,0 //NV_FIRSTAID#First Aid#`
`35,410,1,0,0,0,0,0,0,0,0,0,0 //WE_CALLBABY#Call Baby#`
`35,681,1,0,0,0,0,0,0,0,0,0,0 //ALL_INCCARRY#Enlarge Weight Limit R#`

Please refer to [adding new skills](/adding_new_skills "wikilink") to add new custom skills.

If you do not put them there will be errors

Next, open the file

Look for this:

`620: Ninja`
`621: Summer`

And add your custom class before "Summer"

`620: Ninja`
`621: Summer`
`700: Burglar`

And with that ends the server-side modifications.

Client Side: (XRAY Required unless you plan to replace 3rd class id's.)

first start by editing

Class_tab.txt

Find this

`!52`
`°Ë»ç`
`¸¶¹ý»ç`

Add your custom class

`!35`
`Burglar`
`!52`
`°Ë»ç`
`¸¶¹ý»ç`

Second edit

imf_tab.txt

Find this

`!52`
`°Ë»ç`
`¸¶¹ý»ç`

Add your custom class

`!35`
`¼ºÁ÷ÀÚ`
`!52`
`°Ë»ç`
`¸¶¹ý»ç`

Third edit

reality_dir_tab.txt

Find this

`!52`
`°Ë»ç\\°Ë»ç`
`¸¶¹ý»ç\\¸¶¹ý»ç`

Add your custom class (!35)

`!35`
`¼ºÁ÷ÀÚ\\¼ºÁ÷ÀÚ`
`!52`
`°Ë»ç\\°Ë»ç`
`¸¶¹ý»ç\\¸¶¹ý»ç`

Fourth edit

reality_tab.txt

Find this

`!52`
`°Ë»ç`
`¸¶¹ý»ç`

Add your custom class (!35)

`!35`
`¼ºÁ÷ÀÚ`
`!52`
`°Ë»ç`
`¸¶¹ý»ç`

Fourth edit

monstrosity_tab.txt

Find this

`!47`
`1_M_01`
`1_M_02`
`1_M_03`

Add your custom class ()

`!35`
`Burglar`
`!47`
`1_M_01`
`1_M_02`
`1_M_03`
`1_M_04`

Now copy the sprite files that will go on

Male:

`sprite\ÀÎ°£Á·\¸öÅë\³²`

Female:

`sprite\ÀÎ°£Á·\¸öÅë\¿©`

Male:

`Burglar_³².spr`
`Burglar_³².act`

Female:

`Burglar_¿©.spr`
`Burglar_¿©.act`

[Category:Customization](/Category:Customization "wikilink") [Category:Source Snippets](/Category:Source_Snippets "wikilink")