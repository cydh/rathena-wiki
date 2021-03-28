---
title: @go
permalink: /@go/
---

A lot of people like to change the @go command so that they can add in any new Custom Maps they like or even change the coordinates for old maps. This guide will show you how to add new maps to @go. However, it's extremely easy to change the coordinates of an existing map as well.

<h1>
Adding a New Map to @go

</h1>
Head on over to .../src/map/atcommand.cpp and search for @go so that you'll get this:

` /*==========================================`
`  * @go [city_number or city_name] - Updated by Harbin`
`  *------------------------------------------*/`
` ACMD_FUNC(go)`
` {`
` 	int i;`
` 	int town;`
` 	char map_name[MAP_NAME_LENGTH];`
` ` 
` 	const struct {`
` 		char map[MAP_NAME_LENGTH];`
` 		int x, y;`
` 	} data[] = {`
` 		{ MAP_PRONTERA,    156, 191 }, //  0=Prontera`
` 		{ MAP_MORROC,      156,  93 }, //  1=Morroc`
` 		{ MAP_GEFFEN,      119,  59 }, //  2=Geffen`
` 		{ MAP_PAYON,       162, 233 }, //  3=Payon`
` 		{ MAP_ALBERTA,     192, 147 }, //  4=Alberta`
` #ifdef RENEWAL`
` 		{ MAP_IZLUDE,      128, 146 }, //  5=Izlude (Renewal)`
` #else`
` 		{ MAP_IZLUDE,      128, 114 }, //  5=Izlude`
` #endif`
` 		{ MAP_ALDEBARAN,   140, 131 }, //  6=Al de Baran`
` 		{ MAP_LUTIE,       147, 134 }, //  7=Lutie`
` 		{ MAP_COMODO,      209, 143 }, //  8=Comodo`
` 		{ MAP_YUNO,        157,  51 }, //  9=Yuno`
` 		{ MAP_AMATSU,      198,  84 }, // 10=Amatsu`
` 		{ MAP_GONRYUN,     160, 120 }, // 11=Gonryun`
` 		{ MAP_UMBALA,       89, 157 }, // 12=Umbala`
` 		{ MAP_NIFLHEIM,     21, 153 }, // 13=Niflheim`
` 		{ MAP_LOUYANG,     217,  40 }, // 14=Louyang`
` #ifdef RENEWAL`
` 		{ MAP_NOVICE,       18, 26  }, // 15=Training Grounds (Renewal)`
` #else`
` 		{ MAP_NOVICE,       53, 111 }, // 15=Training Grounds`
` #endif`
` 		{ MAP_JAIL,         23,  61 }, // 16=Prison`
` 		{ MAP_JAWAII,      249, 127 }, // 17=Jawaii`
` 		{ MAP_AYOTHAYA,    151, 117 }, // 18=Ayothaya`
` 		{ MAP_EINBROCH,     64, 200 }, // 19=Einbroch`
` 		{ MAP_LIGHTHALZEN, 158,  92 }, // 20=Lighthalzen`
` 		{ MAP_EINBECH,      70,  95 }, // 21=Einbech`
` 		{ MAP_HUGEL,        96, 145 }, // 22=Hugel`
` 		{ MAP_RACHEL,      130, 110 }, // 23=Rachel`
` 		{ MAP_VEINS,       216, 123 }, // 24=Veins`
` 		{ MAP_MOSCOVIA,    223, 184 }, // 25=Moscovia`
` 		{ MAP_MIDCAMP,     180, 240 }, // 26=Midgard Camp`
` 		{ MAP_MANUK,       282, 138 }, // 27=Manuk`
` 		{ MAP_SPLENDIDE,   201, 147 }, // 28=Splendide`
` 		{ MAP_BRASILIS,    182, 239 }, // 29=Brasilis`
` 		{ MAP_DICASTES,    198, 187 }, // 30=El Dicastes`
` 		{ MAP_MORA,         44, 151 }, // 31=Mora`
` 		{ MAP_DEWATA,      200, 180 }, // 32=Dewata`
` 		{ MAP_MALANGDO,    140, 114 }, // 33=Malangdo Island`
` 		{ MAP_MALAYA,      242, 211 }, // 34=Malaya Port`
` 		{ MAP_ECLAGE,      110,  39 }, // 35=Eclage`
` 		{ MAP_LASAGNA,     193, 182 }, // 36=Lasagna`
` 	};`

Now, for the purpose of this guide, I'll be adding Glast Heim as a map I want in my @go function. Since Eclage is the last map, I will add my new map after Eclage.

So, find:

` { MAP_LASAGNA,     193, 182 }, // 36=Lasagna`

and I will add:

<tab><tab>`{ MAP_GLAST_01,`<tab>`123, 234 }, // 36=Glast Heim`

right after so that it would look like this (after I've **filled** in my **tabs**):

` { MAP_LASAGNA,     193, 182 }, // 36=Lasagna`
` { MAP_GLAST_01,   123, 234 }, // 37=Glast Heim`

Please note that the structure of it is as followed:

<tab><tab>`{ MAP_MAPNAME,`<tab>`Coordinate X, Coordinate Y }, // Number=the location name`

**Note:** *As it's C language and not emulator's scripting language, <tab> mentioned above is not really needed. Tabs in the source is just to make the code visually more appealing.*

<h4>
Getting @go to Work

</h4>
To get the town name as well as with the number working, you need to scroll down a little bit till you see such code:

`	// get possible name of the city`
`	map_name[MAP_NAME_LENGTH-1] = '\0';`
`	for (i = 0; map_name[i]; i++)`
`		map_name[i] = TOLOWER(map_name[i]);`
`	// try to identify the map name`
`	if (strncmp(map_name, "prontera", 3) == 0) {`
`		town = 0;`
`	} else if (strncmp(map_name, "morocc", 4) == 0 ||`
`	           strncmp(map_name, "morroc", 4) == 0) {`
`		town = 1;`
`	} else if (strncmp(map_name, "geffen", 3) == 0) {`
`		town = 2;`
`	} else if (strncmp(map_name, "payon", 3) == 0) {`
`		town = 3;`
`	} else if (strncmp(map_name, "alberta", 3) == 0) {`
`		town = 4;`
`	} else if (strncmp(map_name, "izlude", 3) == 0) {`
`		town = 5;`
`	} else if (strncmp(map_name, "aldebaran", 3) == 0) {`
`		town = 6;`
`	} else if (strncmp(map_name, "lutie", 3) == 0 ||`
`	           strcmp(map_name,  "christmas") == 0 ||`
`	           strncmp(map_name, "xmas", 3) == 0 ||`
`	           strncmp(map_name, "x-mas", 3) == 0) {`
`		town = 7;`
`	} else if (strncmp(map_name, "comodo", 3) == 0) {`
`		town = 8;`
`	} else if (strncmp(map_name, "juno", 3) == 0 ||`
`	           strncmp(map_name, "yuno", 3) == 0) {`
`		town = 9;`
`	} else if (strncmp(map_name, "amatsu", 3) == 0) {`
`		town = 10;`
`	} else if (strncmp(map_name, "kunlun", 3) == 0 ||`
`	           strncmp(map_name, "gonryun", 3) == 0) {`
`		town = 11;`
`	} else if (strncmp(map_name, "umbala", 3) == 0) {`
`		town = 12;`
`	} else if (strncmp(map_name, "niflheim", 3) == 0) {`
`		town = 13;`
`	} else if (strncmp(map_name, "louyang", 3) == 0) {`
`		town = 14;`
`	} else if (strncmp(map_name, "new_1-1", 3) == 0 ||`
`	           strncmp(map_name, "startpoint", 3) == 0 ||`
`	           strncmp(map_name, "beginning", 3) == 0) {`
`		town = 15;`
`	} else if (strncmp(map_name, "sec_pri", 3) == 0 ||`
`	           strncmp(map_name, "prison", 3) == 0 ||`
`	           strncmp(map_name, "jail", 3) == 0) {`
`		town = 16;`
`	} else if (strncmp(map_name, "jawaii", 3) == 0) {`
`		town = 17;`
`	} else if (strncmp(map_name, "ayothaya", 3) == 0) {`
`		town = 18;`
`	} else if (strncmp(map_name, "einbroch", 5) == 0) {`
`		town = 19;`
`	} else if (strncmp(map_name, "lighthalzen", 3) == 0) {`
`		town = 20;`
`	} else if (strncmp(map_name, "einbech", 5) == 0) {`
`		town = 21;`
`	} else if (strncmp(map_name, "hugel", 3) == 0) {`
`		town = 22;`
`	} else if (strncmp(map_name, "rachel", 3) == 0) {`
`		town = 23;`
`	} else if (strncmp(map_name, "veins", 3) == 0) {`
`		town = 24;`
`	} else if (strncmp(map_name, "moscovia", 3) == 0) {`
`		town = 25;`
`	} else if (strncmp(map_name, "mid_camp", 3) == 0) {`
`		town = 26;`
`	} else if (strncmp(map_name, "manuk", 3) == 0) {`
`		town = 27;`
`	} else if (strncmp(map_name, "splendide", 3) == 0) {`
`		town = 28;`
`	} else if (strncmp(map_name, "brasilis", 3) == 0) {`
`		town = 29;`
`	} else if (strncmp(map_name, "dicastes01", 3) == 0) {`
`		town = 30;`
`	} else if (strcmp(map_name,  "mora") == 0) {`
`		town = 31;`
`	} else if (strncmp(map_name, "dewata", 3) == 0) {`
`		town = 32;`
`	} else if (strncmp(map_name, "malangdo", 5) == 0) {`
`		town = 33;`
`	} else if (strncmp(map_name, "malaya", 5) == 0) {`
`		town = 34;`
`	} else if (strncmp(map_name, "eclage", 3) == 0) {`
`		town = 35;`
`	} else if (strncmp(map_name, "lasagna", 2) == 0) {`
`		town = 36;`
`   `**`}`**

Before the last bracket, add the following:

`   } else if (strncmp(map_name, "`<mapname>`", `<number of characters required>`) == 0) {`
`       town = `<town number>`;`

Your "<mapname>" is your map's name while <number of characters required> is the number of characters of the name required to be typed so that the town is recognized in @go.

So, for my Glast Heim map, it would be:

`} else if (strncmp(map_name, "lasagna", 2) == 0) {`
`       town = 36;`
`} else if (strncmp(map_name, "glast_01", 3) == 0) {`
`       town = 37;`
`   }`

<h1>
Working with mapindex.hpp

</h1>
Now, moving forward. Back out from your .../src/map folder and go into .../src/common/mapindex.hpp. Find:

`//Some definitions for the mayor city maps.`
`#define MAP_PRONTERA "prontera"`
`#define MAP_GEFFEN "geffen"`
`#define MAP_MORROC "morocc"`
`#define MAP_ALBERTA "alberta"`
`#define MAP_PAYON "payon"`
`#define MAP_IZLUDE "izlude"`
`#define MAP_ALDEBARAN "aldebaran"`
`#define MAP_LUTIE "xmas"`
`#define MAP_COMODO "comodo"`
`#define MAP_YUNO "yuno"`
`#define MAP_AMATSU "amatsu"`
`#define MAP_GONRYUN "gonryun"`
`#define MAP_UMBALA "umbala"`
`#define MAP_NIFLHEIM "niflheim"`
`#define MAP_LOUYANG "louyang"`
`#define MAP_JAWAII "jawaii"`
`#define MAP_AYOTHAYA "ayothaya"`
`#define MAP_EINBROCH "einbroch"`
`#define MAP_LIGHTHALZEN "lighthalzen"`
`#define MAP_EINBECH "einbech"`
`#define MAP_HUGEL "hugel"`
`#define MAP_RACHEL "rachel"`
`#define MAP_VEINS "veins"`
`#define MAP_JAIL "sec_pri"`
`#ifdef RENEWAL`
`	#define MAP_NOVICE "iz_int"`
`#else`
`	#define MAP_NOVICE "new_1-1"`
`#endif`
`#define MAP_MOSCOVIA "moscovia"`
`#define MAP_MIDCAMP "mid_camp"`
`#define MAP_MANUK "manuk"`
`#define MAP_SPLENDIDE "splendide"`
`#define MAP_BRASILIS "brasilis"`
`#define MAP_DICASTES "dicastes01"`
`#define MAP_MORA "mora"`
`#define MAP_DEWATA "dewata"`
`#define MAP_MALANGDO "malangdo"`
`#define MAP_MALAYA "malaya"`
`#define MAP_ECLAGE "eclage"`
`#define MAP_ECLAGE_IN "ecl_in01"`
`#define MAP_LASAGNA "lasagna"`

The structure for this is as followed:

`#define MAP_MAPNAME "mapname"`

In the case of me adding my map, I will do it as so:

`#define MAP_GLAST_01 "glast_01"`

So that it would look like:

`#define MAP_LASAGNA "lasagna"`
`#define MAP_GLAST_01 "glast_01"`

**Note**: There are no tabs

Now, save the source files and recompile the server. And you will have your own custom @go location.

<h1>
Additional Steps

</h1>
If you want your map to show up in @go when you do @go, you would need to add it to one more file and this file is called the [atcommands.yml](https://github.com/rathena/rathena/blob/master/conf/atcommands.yml). You can find such file by heading to .../conf/atcommands.yml. Search for **go:** so that you can find this code:

`  - Command: go`
`    Help: |`
`      Params: <city name|number>`
`      Warps you to a city.`
`      -3: (Memo point 2)  14: louyang         31: mora`
`      -2: (Memo point 1)  15: start point     32: dewata`
`      -1: (Memo point 0)  16: prison/jail     33: malangdo island`
`       0: prontera              17: jawaii             34: malaya port`
`       1: morocc                18: ayothaya       35: eclage`
`       2: geffen                  19: einbroch       36: lasagna`
`       3: payon                  20: lighthalzen`
`       4: alberta                 21: einbech`
`       5: izlude                   22: hugel`
`       6: aldebaran           23: rachel`
`       7: xmas (lutie)        24: veins`
`       8: comodo               25: moscovia`
`       9: yuno                     26: midgard camp`
`      10: amatsu               27: manuk`
`      11: gonryun              28: splendide`
`      12: umbala               29: brasilis`
`      13: niflheim              30: el dicastes`

Now, since I want to keep the structure of my maps still intact, I will add my new map right after Eclage once again. To do so, I will just expand the line where geffen and einbroch are by doing such:

`       3: payon                  20: lighthalzen    `**`37:` `glast` `heim\n"`**

So that after I'm done it would look like this:

`  - Command: go`
`    Help: |`
`      Params: <city name|number>`
`      Warps you to a city.`
`      -3: (Memo point 2)  14: louyang         31: mora`
`      -2: (Memo point 1)  15: start point     32: dewata`
`      -1: (Memo point 0)  16: prison/jail     33: malangdo island`
`       0: prontera              17: jawaii             34: malaya port`
`       1: morocc                18: ayothaya       35: eclage`
`       2: geffen                  19: einbroch       36: lasagna`
`       3: payon                  20: lighthalzen    `**`37:` `glast` `heim\n"`**
`       4: alberta                 21: einbech`
`       5: izlude                   22: hugel`
`       6: aldebaran           23: rachel`
`       7: xmas (lutie)        24: veins`
`       8: comodo               25: moscovia`
`       9: yuno                     26: midgard camp`
`      10: amatsu               27: manuk`
`      11: gonryun              28: splendide`
`      12: umbala               29: brasilis`
`      13: niflheim              30: el dicastes`

**Note:** *Make sure that you align everything by adding spaces!* [Category:Source Snippets](/Category:Source_Snippets "wikilink") [Category:Customization](/Category:Customization "wikilink")
