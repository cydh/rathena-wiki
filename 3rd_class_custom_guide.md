---
title: 3rd class custom guide
permalink: /3rd_class_custom_guide/
---

Source
------

    Index: trunk/src/common/mmo.h
    ===================================================================
    --- trunk/src/common/mmo.h  (revision 14435)
    +++ trunk/src/common/mmo.h  (working copy)
    @@ -85,7 +85,7 @@
     #define MAX_ZENY 1000000000
     #define MAX_FAME 1000000000
     #define MAX_CART 100
    -#define MAX_SKILL 1020
    +#define MAX_SKILL 2520
     #define GLOBAL_REG_NUM 256
     #define ACCOUNT_REG_NUM 64
     #define ACCOUNT_REG2_NUM 16
    @@ -637,6 +637,42 @@
        JOB_STAR_GLADIATOR,
        JOB_STAR_GLADIATOR2,
        JOB_SOUL_LINKER,
    +
    +   JOB_RUNE_KNIGHT = 4054,
    +   JOB_WARLOCK,
    +   JOB_RANGER,
    +   JOB_ARCHBISHOP,
    +   JOB_MECHANIC,
    +   JOB_GUILLOTINE_CROSS,
    +   JOB_RUNE_KNIGHT_H,
    +   JOB_WARLOCK_H,
    +   JOB_RANGER_H,
    +   JOB_ARCHBISHOP_H,
    +   JOB_MECHANIC_H,
    +   JOB_GUILLOTINE_CROSS_H,
    +
    +   JOB_ROYAL_GUARD, // 4066
    +   JOB_SORCERER,
    +   JOB_MINSTREL,
    +   JOB_WANDERER,
    +   JOB_SHURA,
    +   JOB_GENETIC,
    +   JOB_SHADOW_CHASER,
    +   JOB_ROYAL_GUARD_H,
    +   JOB_SORCERER_H,
    +   JOB_MINSTREL_H,
    +   JOB_WANDERER_H,
    +   JOB_SHURA_H,
    +   JOB_GENETIC_H,
    +   JOB_SHADOW_CHASER_H,
    +
    +   JOB_RUNE_KNIGHT2, // 4080
    +   JOB_RUNE_KNIGHT2_H,
    +   JOB_ROYAL_GUARD2,
    +   JOB_ROYAL_GUARD2_H,
    +   JOB_RANGER2,
    +   JOB_RANGER2_H,
    +
        JOB_MAX,
     };

    Index: trunk/src/map/atcommand.c
    ===================================================================
    --- trunk/src/map/atcommand.c   (revision 14435)
    +++ trunk/src/map/atcommand.c   (working copy)
    @@ -1327,6 +1327,19 @@
                { "taekwon girl",   4046 },
                { "star gladiator", 4047 },
                { "soul linker",    4049 },
    +           { "rune knight",    4054 },
    +           { "warlock",        4055 },
    +           { "ranger",         4056 },
    +           { "archbishop",     4057 },
    +           { "mechanic",       4058 },
    +           { "guillotine cross",   4059 },
    +           { "royal guard",    4066 },
    +           { "sorcerer",       4067 },
    +           { "minstrel",       4068 },
    +           { "wanderer",       4069 },
    +           { "shura",          4070 },
    +           { "genetic",        4071 },
    +           { "shadow chaser",  4072 },
            };

            for (i=0; i < ARRAYLENGTH(jobs); i++) {
    @@ -1361,6 +1374,10 @@
                clif_displaymessage(fd, "4027 Baby Acolyte   4034 Baby Hunter      4041 Baby Alchemist 4048 N/A");
                clif_displaymessage(fd, "4028 Baby Merchant  4035 Baby Assassin    4042 Baby Bard      4049 Soul Linker");
                clif_displaymessage(fd, "4029 Baby Thief     4036 N/A              4043 Baby Dancer");
    +           clif_displaymessage(fd, "4054 Rune Knight    4055 Warlock          4056 Ranger");
    +           clif_displaymessage(fd, "4057 Archbishop     4058 Mechanic         4059 Guillotine Cross");
    +           clif_displaymessage(fd, "4066 Royal Guard    4067 Sorcerer         4068 Minstrel       4069 Wanderer");
    +           clif_displaymessage(fd, "4070 Shura           4071 Genetic          4072 Shadow Chaser");
                clif_displaymessage(fd, "[upper]: -1 (default) to automatically determine the 'level', 0 to force normal job, 1 to force high job.");
                return -1;
            }
    @@ -4478,26 +4495,29 @@
     {
        nullpo_retr(-1, sd);

    -   if (!pc_isriding(sd)) { // if actually no peco
    -       if (!pc_checkskill(sd, KN_RIDING))
    -       {
    -           clif_displaymessage(fd, msg_txt(213)); // You can not mount a Peco Peco with your current job.
    +   if (pc_isriding(sd) || pc_isridingdragon(sd) || pc_isridingwarg(sd)) {  //Dismount
    +       pc_setoption(sd, sd->sc.option & ~(OPTION_RIDING | OPTION_RIDING_DRAGON | OPTION_RIDING_WARG));
    +       clif_displaymessage(fd, msg_txt(214)); // You have released your Peco Peco.
    +   } else {
    +       if (sd->disguise){
    +           clif_displaymessage(fd, msg_txt(212)); // Cannot mount a Peco Peco while in disguise.
                return -1;
            }
    -
    -       if (sd->disguise)
    -       {
    -           clif_displaymessage(fd, msg_txt(212)); // Cannot mount a Peco Peco while in disguise.
    +       if(pc_checkskill(sd, RK_DRAGONTRAINING)){
    +           pc_setoption(sd, sd->sc.option | OPTION_RIDING_DRAGON); //3rdriding
    +       }
    +       else if(pc_checkskill(sd, KN_RIDING)){
    +           pc_setoption(sd, sd->sc.option | OPTION_RIDING);
    +           clif_displaymessage(fd, msg_txt(102)); // You have mounted a Peco Peco.
    +       }
    +       else if(pc_checkskill(sd, RA_WUGRIDER)){
    +           pc_setoption(sd, sd->sc.option | OPTION_RIDING_WARG);
    +       }
    +       else {
    +           clif_displaymessage(fd, msg_txt(213)); // You can not mount a Peco Peco with your current job.
                return -1;
            }
    -
    -       pc_setoption(sd, sd->sc.option | OPTION_RIDING);
    -       clif_displaymessage(fd, msg_txt(102)); // You have mounted a Peco Peco.
    -   } else {    //Dismount
    -       pc_setoption(sd, sd->sc.option & ~OPTION_RIDING);
    -       clif_displaymessage(fd, msg_txt(214)); // You have released your Peco Peco.
    -   }
    -
    +   }
        return 0;
     }

    Index: trunk/src/map/script.c
    ===================================================================
    --- trunk/src/map/script.c  (revision 14435)
    +++ trunk/src/map/script.c  (working copy)
    @@ -7008,7 +7008,7 @@
            flag = script_getnum(st,3);
        else if( !option ){// Request to remove everything.
            flag = 0;
    -       option = OPTION_CART|OPTION_FALCON|OPTION_RIDING;
    +       option = OPTION_CART|OPTION_FALCON|OPTION_RIDING|OPTION_RIDING_DRAGON|OPTION_WARG|OPTION_RIDING_WARG;
        }
        if( flag ){// Add option
            if( option&OPTION_WEDDING && !battle_config.wedding_modifydisplay )
    Index: trunk/src/map/skill.h
    ===================================================================
    --- trunk/src/map/skill.h   (revision 14435)
    +++ trunk/src/map/skill.h   (working copy)
    @@ -1006,6 +1006,226 @@
        SA_ELEMENTFIRE,
        SA_ELEMENTWIND,

    +   // Rune Knight
    +   RK_ENCHANTBLADE = 2001,
    +   RK_SONICWAVE,
    +   RK_DEATHBOUND,
    +   RK_HUNDREDSPEAR,
    +   RK_WINDCUTTER,
    +   RK_IGNITIONBREAK,
    +   RK_DRAGONTRAINING,
    +   RK_DRAGONBREATH,
    +   RK_DRAGONHOWLING,
    +   RK_RUNEMASTERY,
    +   RK_MILLENNIUMSHIELD,
    +   RK_CRUSHSTRIKE,
    +   RK_REFRESH,
    +   RK_GIANTGROWTH,
    +   RK_STONEHARDSKIN,
    +   RK_VITALITYACTIVATION,
    +   RK_STORMBLAST,
    +   RK_FIGHTINGSPIRIT,
    +   RK_ABUNDANCE,
    +   RK_PHANTOMTHRUST,
    +
    +   // Guillotine Cross
    +   GC_VENOMIMPRESS = 2021,
    +   GC_CROSSIMPACT,
    +   GC_DARKILLUSION,
    +   GC_RESEARCHNEWPOISON,
    +   GC_CREATENEWPOISON,
    +   GC_ANTIDOTE,
    +   GC_POISONINGWEAPON,
    +   GC_WEAPONBLOCKING,
    +   GC_COUNTERSLASH,
    +   GC_WEAPONCRUSH,
    +   GC_VENOMPRESSURE,
    +   GC_POISONSMOKE,
    +   GC_CLOAKINGEXCEED,
    +   GC_PHANTOMMENACE,
    +   GC_HALLUCINATIONWALK,
    +   GC_ROLLINGCUTTER,
    +   GC_CROSSRIPPERSLASHER,
    +
    +   // Arch Bishop
    +   AB_JUDEX = 2038,
    +   AB_ANCILLA,
    +   AB_ADORAMUS,
    +   AB_CLEMENTIA,
    +   AB_CANTO,
    +   AB_CHEAL,
    +   AB_EPICLESIS,
    +   AB_PRAEFATIO,
    +   AB_ORATIO,
    +   AB_LAUDAAGNUS,
    +   AB_LAUDARAMUS,
    +   AB_EUCHARISTICA,
    +   AB_HIGHNESSHEAL,
    +   AB_CLEARANCE,
    +   AB_EXPIATIO,
    +   AB_DUPLELIGHT,
    +   AB_SILENTIUM,
    +   AB_DUPLELIGHT_MELEE,
    +   AB_DUPLELIGHT_MAGIC,
    +
    +   // Warlock
    +   WL_WHITEIMPRISON = 2201,
    +   WL_SOULEXPANSION,
    +   WL_FROSTMISTY,
    +   WL_JACKFROST,
    +   WL_MARSHOFABYSS,
    +   WL_RECOGNIZEDSPELL,
    +   WL_SIENNAEXECRATE,
    +   WL_RADIUS,
    +   WL_STASIS,
    +   WL_DRAINLIFE,
    +   WL_CRIMSONROCK,
    +   WL_HELLINFERNO,
    +   WL_COMET,
    +   WL_CHAINLIGHTNING,
    +   WL_CHAINLIGHTNING_ATK,
    +   WL_EARTHSTRAIN,
    +   WL_TETRAVORTEX,
    +   WL_TETRAVORTEX_FIRE,
    +   WL_TETRAVORTEX_WATER,
    +   WL_TETRAVORTEX_WIND,
    +   WL_TETRAVORTEX_GROUND,
    +   WL_SUMMONFB,
    +   WL_SUMMONBL,
    +   WL_SUMMONWB,
    +   WL_SUMMON_ATK_FIRE,
    +   WL_SUMMON_ATK_WIND,
    +   WL_SUMMON_ATK_WATER,
    +   WL_SUMMON_ATK_GROUND,
    +   WL_SUMMONSTONE,
    +   WL_RELEASE,
    +
    +   // Ranger
    +   RA_ARROWSTORM = 2233,
    +   RA_FEARBREEZE,
    +   RA_RANGERMAIN,
    +   RA_AIMEDBOLT,
    +   RA_DETONATOR,
    +   RA_ELECTRICSHOCKER,
    +   RA_CLUSTERBOMB,
    +   RA_WUGMASTERY,
    +   RA_WUGRIDER,
    +   RA_WUGDASH,
    +   RA_WUGSTRIKE,
    +   RA_WUGBITE,
    +   RA_TOOTHOFWUG,
    +   RA_SENSITIVEKEEN,
    +   RA_CAMOUFLAGE,
    +   RA_RESEARCHTRAP,
    +   RA_MAGENTATRAP,
    +   RA_COBALTTRAP,
    +   RA_MAIZETRAP,
    +   RA_VERDURETRAP,
    +   RA_FIRINGTRAP,
    +   RA_ICEBOUNDTRAP,
    +
    +   // Mechanic
    +   NC_MADOLICENCE = 2255,
    +   NC_BOOSTKNUCKLE,
    +   NC_PILEBUNKER,
    +   NC_VULCANARM,
    +   NC_FLAMELAUNCHER,
    +   NC_COLDSLOWER,
    +   NC_ARMSCANNON,
    +   NC_ACCELERATION,
    +   NC_HOVERING,
    +   NC_F_SIDESLIDE,
    +   NC_B_SIDESLIDE,
    +   NC_MAINFRAME,
    +   NC_SELFDESTRUCTION,
    +   NC_SHAPESHIFT,
    +   NC_EMERGENCYCOOL,
    +   NC_INFRAREDSCAN,
    +   NC_ANALYZE,
    +   NC_MAGNETICFIELD,
    +   NC_NEUTRALBARRIER,
    +   NC_STEALTHFIELD,
    +   NC_REPAIR,
    +   NC_TRAININGAXE,
    +   NC_RESEARCHFE,
    +   NC_AXEBOOMERANG,
    +   NC_POWERSWING,
    +   NC_AXETORNADO,
    +   NC_SILVERSNIPER,
    +   NC_MAGICDECOY,
    +   NC_DISJOINT,
    +   // missing
    +
    +   // Shadow Chaser
    +   SC_REPRODUCE = 2285,
    +   SC_BODYPAINT,
    +   SC_AUTOSHADOWSPELL,
    +   SC_SHADOWFORM,
    +   SC_TRIANGLESHOT,
    +   SC_INVISIBILITY,
    +   SC_DEADLYINFECT,
    +   SC_ENERVATION,
    +   SC_GROOMY,
    +   SC_IGNORANCE,
    +   SC_LAZYNESS,
    +   SC_UNLUCKY,
    +   SC_WEAKNESS,
    +   SC_STRIPACCESSORY,
    +   SC_MANHOLE,
    +   SC_DIMENSIONDOOR,
    +   SC_MAELSTROM,
    +   SC_BLOODYLUST,
    +   SC_FEINTBOMB,
    +
    +   // Wanderer
    +   WA_SWINGDANCE,
    +   WA_SYMPHONY_OF_LOVER,
    +
    +   // Shura
    +   SR_SKYNETBLOW,
    +   SR_EARTHSHAKER,
    +   SR_FALLENEMPIRE,
    +   SR_TIGERCANNON,
    +   SR_HELLGATE,
    +   SR_RAMPAGEBLASTER,
    +   SR_CRESCENTELBOW,
    +   SR_CURSEDCIRCLE,
    +   SR_LIGHTNINGWALK,
    +   SR_KNUCKLEARROW,
    +   SR_WINDMILL,
    +   SR_RAISINGDRAGON,
    +   SR_GENTLETOUCH,
    +   SR_ASSIMILATEPOWER,
    +   SR_POWERVELOCITY,
    +   SR_CRESCENTELBOW_AUTOSPELL,
    +   SR_GATEOFHELL,
    +   SR_GENTLETOUCH_QUIET,
    +   SR_GENTLETOUCH_CURE,
    +   SR_GENTLETOUCH_ENERGYGAIN,
    +   SR_GENTLETOUCH_CHANGE,
    +   SR_GENTLETOUCH_REVITALIZE,
    +
    +   // Royal Guard
    +   LG_CANNONSPEAR,
    +   LG_BANISHINGPOINT,
    +   LG_TRAMPLE,
    +   LG_SHIELDPRESS,
    +   LG_REFLECTDAMAGE,
    +   LG_PINPOINTATACK,
    +   LG_FORCEOFVANGUARD,
    +   LG_RAGEBURST,
    +   LG_SHIELDSPELL,
    +   LG_EXEEDBREAK,
    +   LG_OVERBRAND,
    +   LG_PRESTIGE,
    +   LG_BANDING,
    +   LG_MOONSLASHER,
    +   LG_RAYOFGENESIS,
    +   LG_PIETY,
    +   LG_EARTHDRIVE,
    +   LG_HESPERUSLIT,
    +   LG_INSPIRATION,
    +
        HLIF_HEAL = 8001,
        HLIF_AVOID,
        HLIF_BRAIN,
    Index: trunk/src/map/clif.c
    ===================================================================
    --- trunk/src/map/clif.c    (revision 14435)
    +++ trunk/src/map/clif.c    (working copy)
    @@ -8613,6 +8613,15 @@
            if (sd->sc.option&OPTION_RIDING)
                clif_status_load(&sd->bl, SI_RIDING, 1);

    +       if (sd->sc.option&OPTION_RIDING_DRAGON)
    +           clif_status_load(&sd->bl, SI_RIDING, 1);
    +
    +       if (sd->sc.option&OPTION_WARG)
    +           clif_status_load(&sd->bl, SI_WUG, 1);
    +
    +       if (sd->sc.option&OPTION_RIDING_WARG)
    +           clif_status_load(&sd->bl, SI_RIDING, 1);
    +
            if(sd->status.manner < 0)
                sc_start(&sd->bl,SC_NOCHAT,100,0,0);

    @@ -9874,8 +9883,8 @@
      *------------------------------------------*/
     void clif_parse_RemoveOption(int fd,struct map_session_data *sd)
     {
    -   //Can only remove Cart/Riding/Falcon.
    -   pc_setoption(sd,sd->sc.option&~(OPTION_CART|OPTION_RIDING|OPTION_FALCON));
    +   //Can only remove Cart/Riding/Falcon/Dragon/Warg.
    +   pc_setoption(sd,sd->sc.option&~(OPTION_CART|OPTION_RIDING|OPTION_FALCON|OPTION_RIDING_DRAGON|OPTION_WARG|OPTION_RIDING_WARG)); //3rdriding
     }

     /*==========================================
    Index: trunk/src/map/status.c
    ===================================================================
    --- trunk/src/map/status.c  (revision 14435)
    +++ trunk/src/map/status.c  (working copy)
    @@ -4428,6 +4428,24 @@
                    case JOB_BABY_CRUSADER:
                        class_ = JOB_BABY_CRUSADER2;
                        break;
    +               case JOB_RUNE_KNIGHT:
    +                   class_ = JOB_RUNE_KNIGHT2;
    +                   break;
    +               case JOB_RUNE_KNIGHT_H:
    +                   class_ = JOB_RUNE_KNIGHT2_H;
    +                   break;
    +               case JOB_ROYAL_GUARD:
    +                   class_ = JOB_ROYAL_GUARD2;
    +                   break;
    +               case JOB_ROYAL_GUARD_H:
    +                   class_ = JOB_ROYAL_GUARD2_H;
    +                   break;
    +               case JOB_RANGER:
    +                   class_ = JOB_RANGER2;
    +                   break;
    +               case JOB_RANGER_H:
    +                   class_ = JOB_RANGER2_H;
    +                   break;
                    }
                    sd->vd.class_ = class_;
                    clif_get_weapon_view(sd, &sd->vd.weapon, &sd->vd.shield);
    Index: trunk/src/map/status.h
    ===================================================================
    --- trunk/src/map/status.h  (revision 14435)
    +++ trunk/src/map/status.h  (working copy)
    @@ -651,6 +651,15 @@
        SI_CASH_PLUSONLYJOBEXP = 312,
     // SI_PARTYFLEE = 313,
     // SI_ANGEL_PROTECT = 314,
    +   SI_ENCHANTBLADE = 316,
    +
    +   SI_NAUTHIZ = 318, // Rune Mastery lvl 8
    +   SI_TURISSUS = 319, // Rune Mastery lvl 1
    +   SI_HAGALAZ = 320, // Rune Mastery lvl 4
    +   SI_ISHA = 321, // Rune Mastery lvl 2
    +   SI_EISIR = 322, // Rune Mastery lvl 10?
    +   SI_URUZ = 323, // Rune Mastery lvl 6
    +   SI_WUG = 357,
     /*
        SI_ENDURE_MDEF = 315,
        SI_ENCHANTBLADE = 316,
    @@ -1014,6 +1023,9 @@
        OPTION_XMAS      = 0x00010000,
        OPTION_TRANSFORM = 0x00020000,
        OPTION_SUMMER    = 0x00040000,
    +   OPTION_RIDING_DRAGON = 0x00080000,
    +   OPTION_WARG      = 0x00100000,
    +   OPTION_RIDING_WARG = 0x00200000,
     };

     #define OPTION_CART (OPTION_CART1|OPTION_CART2|OPTION_CART3|OPTION_CART4|OPTION_CART5)
    Index: trunk/src/map/pc.c
    ===================================================================
    --- trunk/src/map/pc.c  (revision 14435)
    +++ trunk/src/map/pc.c  (working copy)
    @@ -440,7 +440,7 @@

        //Only copy the Cart/Peco/Falcon options, the rest are handled via
        //status change load/saving. [Skotlex]
    -   sd->status.option = sd->sc.option&(OPTION_CART|OPTION_FALCON|OPTION_RIDING);
    +   sd->status.option = sd->sc.option&(OPTION_CART|OPTION_FALCON|OPTION_RIDING|OPTION_RIDING_DRAGON|OPTION_WARG|OPTION_RIDING_WARG);

        if (sd->sc.data[SC_JAILED])
        {   //When Jailed, do not move last point.
    @@ -4429,6 +4429,87 @@
            case JOB_SUMMER:
                class_ = MAPID_SUMMER;
                break;
    +       // Renewal
    +       case JOB_RUNE_KNIGHT:
    +       case JOB_RUNE_KNIGHT2:
    +           class_ = MAPID_RUNE_KNIGHT;
    +           break;
    +       case JOB_WARLOCK:
    +           class_ = MAPID_WARLOCK;
    +           break;
    +       case JOB_RANGER:
    +       case JOB_RANGER2:
    +           class_ = MAPID_RANGER;
    +           break;
    +       case JOB_ARCHBISHOP:
    +           class_ = MAPID_ARCHBISHOP;
    +           break;
    +       case JOB_MECHANIC:
    +           class_ = MAPID_MECHANIC;
    +           break;
    +       case JOB_GUILLOTINE_CROSS:
    +           class_ = MAPID_GUILLOTINE_CROSS;
    +           break;
    +       case JOB_RUNE_KNIGHT_H:
    +       case JOB_RUNE_KNIGHT2_H:
    +           class_ = MAPID_RUNE_KNIGHT_H;
    +           break;
    +       case JOB_WARLOCK_H:
    +           class_ = MAPID_WARLOCK_H;
    +           break;
    +       case JOB_RANGER_H:
    +       case JOB_RANGER2_H:
    +           class_ = MAPID_RANGER_H;
    +           break;
    +       case JOB_ARCHBISHOP_H:
    +           class_ = MAPID_ARCHBISHOP_H;
    +           break;
    +       case JOB_MECHANIC_H:
    +           class_ = MAPID_MECHANIC_H;
    +           break;
    +       case JOB_GUILLOTINE_CROSS_H:
    +           class_ = MAPID_GUILLOTINE_CROSS_H;
    +           break;
    +       case JOB_ROYAL_GUARD:
    +       case JOB_ROYAL_GUARD2:
    +           class_ = MAPID_ROYAL_GUARD;
    +           break;
    +       case JOB_SORCERER:
    +           class_ = MAPID_SORCERER;
    +           break;
    +       case JOB_MINSTREL:
    +       case JOB_WANDERER:
    +           class_ = MAPID_MINSTRELWANDERER;
    +           break;
    +       case JOB_SHURA:
    +           class_ = MAPID_SHURA;
    +           break;
    +       case JOB_GENETIC:
    +           class_ = MAPID_GENETIC;
    +           break;
    +       case JOB_SHADOW_CHASER:
    +           class_ = MAPID_SHADOW_CHASER;
    +           break;
    +       case JOB_ROYAL_GUARD_H:
    +       case JOB_ROYAL_GUARD2_H:
    +           class_ = MAPID_ROYAL_GUARD_H;
    +           break;
    +       case JOB_SORCERER_H:
    +           class_ = MAPID_SORCERER_H;
    +           break;
    +       case JOB_MINSTREL_H:
    +       case JOB_WANDERER_H:
    +           class_ = MAPID_MINSTRELWANDERER_H;
    +           break;
    +       case JOB_SHURA_H:
    +           class_ = MAPID_SHURA_H;
    +           break;
    +       case JOB_GENETIC_H:
    +           class_ = MAPID_GENETIC_H;
    +           break;
    +       case JOB_SHADOW_CHASER_H:
    +           class_ = MAPID_SHADOW_CHASER_H;
    +           break;
            default:
                return -1;
        }
    @@ -4514,6 +4595,34 @@
            case MAPID_BABY_MONK:       return JOB_BABY_MONK;
            case MAPID_BABY_ALCHEMIST:  return JOB_BABY_ALCHEMIST;
            case MAPID_BABY_ROGUE:      return JOB_BABY_ROGUE;
    +   //3_1 renewal
    +       case MAPID_RUNE_KNIGHT:     return JOB_RUNE_KNIGHT;
    +       case MAPID_WARLOCK:         return JOB_WARLOCK;
    +       case MAPID_RANGER:          return JOB_RANGER;
    +       case MAPID_ARCHBISHOP:      return JOB_ARCHBISHOP;
    +       case MAPID_MECHANIC:        return JOB_MECHANIC;
    +       case MAPID_GUILLOTINE_CROSS:return JOB_GUILLOTINE_CROSS;
    +   //3_1 advanced renewal
    +       case MAPID_RUNE_KNIGHT_H:   return JOB_RUNE_KNIGHT_H;
    +       case MAPID_WARLOCK_H:       return JOB_WARLOCK_H;
    +       case MAPID_RANGER_H:        return JOB_RANGER_H;
    +       case MAPID_ARCHBISHOP_H:    return JOB_ARCHBISHOP_H;
    +       case MAPID_MECHANIC_H:      return JOB_MECHANIC_H;
    +       case MAPID_GUILLOTINE_CROSS_H: return JOB_GUILLOTINE_CROSS_H;
    +   //3_2 renewal
    +       case MAPID_ROYAL_GUARD:     return JOB_ROYAL_GUARD;
    +       case MAPID_SORCERER:        return JOB_SORCERER;
    +       case MAPID_MINSTRELWANDERER:        return sex?JOB_MINSTREL:JOB_WANDERER;
    +       case MAPID_SHURA:            return JOB_SHURA;
    +       case MAPID_GENETIC:         return JOB_GENETIC;
    +       case MAPID_SHADOW_CHASER:   return JOB_SHADOW_CHASER;
    +   //3_2 advanced renewal
    +       case MAPID_ROYAL_GUARD_H:   return JOB_ROYAL_GUARD_H;
    +       case MAPID_SORCERER_H:      return JOB_SORCERER_H;
    +       case MAPID_MINSTRELWANDERER_H:        return sex?JOB_MINSTREL_H:JOB_WANDERER_H;
    +       case MAPID_SHURA_H:          return JOB_SHURA_H;
    +       case MAPID_GENETIC_H:       return JOB_GENETIC_H;
    +       case MAPID_SHADOW_CHASER_H: return JOB_SHADOW_CHASER_H;
            default:
                return -1;
        }
    @@ -4645,6 +4754,51 @@
            return msg_txt(619);
        case JOB_NINJA:
            return msg_txt(620);
    +   case JOB_RUNE_KNIGHT:
    +   case JOB_RUNE_KNIGHT2:
    +   case JOB_RUNE_KNIGHT_H:
    +   case JOB_RUNE_KNIGHT2_H:
    +       return msg_txt(625);
    +   case JOB_WARLOCK:
    +   case JOB_WARLOCK_H:
    +       return msg_txt(626);
    +   case JOB_RANGER:
    +   case JOB_RANGER2:
    +   case JOB_RANGER_H:
    +   case JOB_RANGER2_H:
    +       return msg_txt(627);
    +   case JOB_ARCHBISHOP:
    +   case JOB_ARCHBISHOP_H:
    +       return msg_txt(628);
    +   case JOB_MECHANIC:
    +   case JOB_MECHANIC_H:
    +       return msg_txt(629);
    +   case JOB_GUILLOTINE_CROSS:
    +   case JOB_GUILLOTINE_CROSS_H:
    +       return msg_txt(630);
    +   case JOB_ROYAL_GUARD:
    +   case JOB_ROYAL_GUARD2:
    +   case JOB_ROYAL_GUARD_H:
    +   case JOB_ROYAL_GUARD2_H:
    +       return msg_txt(631);
    +   case JOB_SORCERER:
    +   case JOB_SORCERER_H:
    +       return msg_txt(632);
    +   case JOB_MINSTREL:
    +   case JOB_MINSTREL_H:
    +       return msg_txt(633);
    +   case JOB_WANDERER:
    +   case JOB_WANDERER_H:
    +       return msg_txt(634);
    +   case JOB_SHURA:
    +   case JOB_SHURA_H:
    +       return msg_txt(635);
    +   case JOB_GENETIC:
    +   case JOB_GENETIC_H:
    +       return msg_txt(636);
    +   case JOB_SHADOW_CHASER:
    +   case JOB_SHADOW_CHASER_H:
    +       return msg_txt(637);

        default:
            return msg_txt(650);
    @@ -6221,10 +6375,16 @@
        pc_calc_skilltree(sd);
        clif_skillinfoblock(sd);

    -   //Remove peco/cart/falcon
    +   //Remove peco/cart/falcon/Dragon
        i = sd->sc.option;
        if(i&OPTION_RIDING && !pc_checkskill(sd, KN_RIDING))
            i&=~OPTION_RIDING;
    +   if (i&OPTION_RIDING_DRAGON && !pc_checkskill(sd, RK_DRAGONTRAINING))
    +       i&=~OPTION_RIDING_DRAGON;
    +   if (i&OPTION_WARG && !pc_checkskill(sd, RA_WUGMASTERY))
    +       i&=~OPTION_WARG;
    +   if (i&OPTION_RIDING_WARG && !pc_checkskill(sd, RA_WUGRIDER))
    +       i&=~OPTION_RIDING_WARG;
        if(i&OPTION_CART && !pc_checkskill(sd, MC_PUSHCART))
            i&=~OPTION_CART;
        if(i&OPTION_FALCON && !pc_checkskill(sd, HT_FALCON))
    @@ -6369,6 +6529,42 @@
            clif_status_load(&sd->bl,SI_RIDING,0);
            status_calc_pc(sd,0); //Mounting/Umounting affects walk and attack speeds.
        }
    +   if( type&OPTION_RIDING_DRAGON && !(p_type&OPTION_RIDING_DRAGON) && (sd->class_&MAPID_BASEMASK) == MAPID_SWORDMAN )  // 3rdriding
    +   {
    +       new_look = -1;
    +       clif_status_load(&sd->bl,SI_RIDING,1);
    +       status_calc_pc(sd,0);
    +   }
    +   else if(!(type&OPTION_RIDING_DRAGON) && p_type&OPTION_RIDING_DRAGON && (sd->class_&MAPID_BASEMASK) == MAPID_SWORDMAN )
    +   {
    +       new_look = -1;
    +       clif_status_load(&sd->bl,SI_RIDING,0);
    +       status_calc_pc(sd,0);
    +   }
    +   if( type&OPTION_RIDING_WARG && !(p_type&OPTION_RIDING_WARG) && (sd->class_&MAPID_BASEMASK) == MAPID_ARCHER )
    +   {
    +       new_look = -1;
    +       clif_status_load(&sd->bl,SI_WUG,1);
    +       status_calc_pc(sd,0);
    +   }
    +   else if(!(type&OPTION_RIDING_WARG) && p_type&OPTION_RIDING_WARG && (sd->class_&MAPID_BASEMASK) == MAPID_ARCHER )
    +   {
    +       new_look = -1;
    +       clif_status_load(&sd->bl,SI_WUG,0);
    +       status_calc_pc(sd,0);
    +   }
    +   if( type&OPTION_WARG && !(p_type&OPTION_WARG) && (sd->class_&MAPID_BASEMASK) == MAPID_ARCHER )
    +   {
    +       new_look = -1;
    +       clif_status_load(&sd->bl,SI_WUG,1);
    +       status_calc_pc(sd,0);
    +   }
    +   else if(!(type&OPTION_WARG) && p_type&OPTION_WARG && (sd->class_&MAPID_BASEMASK) == MAPID_ARCHER )
    +   {
    +       new_look = -1;
    +       clif_status_load(&sd->bl,SI_WUG,0);
    +       status_calc_pc(sd,0);
    +   }

        if(type&OPTION_CART && !(p_type&OPTION_CART))
        { //Cart On
    @@ -6472,10 +6668,14 @@
     int pc_setriding(TBL_PC* sd, int flag)
     {
        if( flag ){
    -       if( pc_checkskill(sd,KN_RIDING) > 0 ) // ‰CfB“OXL‹ŹŠŽť
    +       if( pc_checkskill(sd,RK_DRAGONTRAINING) > 0 )
    +           pc_setoption(sd, sd->sc.option|OPTION_RIDING_DRAGON);
    +       else if( pc_checkskill(sd,KN_RIDING) > 0 ) // ‰CfB“OXL‹ŹŠŽť
                pc_setoption(sd, sd->sc.option|OPTION_RIDING);
    -   } else if( pc_isriding(sd) ){
    -       pc_setoption(sd, sd->sc.option&~OPTION_RIDING);
    +       else if( pc_checkskill(sd,RA_WUGRIDER) > 0 ) // Warg
    +           pc_setoption(sd, sd->sc.option|OPTION_RIDING_WARG);
    +   } else if( pc_isriding(sd) || pc_isridingdragon(sd)){
    +       pc_setoption(sd, sd->sc.option&~(OPTION_RIDING|OPTION_RIDING_DRAGON|OPTION_WARG|OPTION_RIDING_WARG));
        }

        return 0;
    Index: trunk/src/map/pc.h
    ===================================================================
    --- trunk/src/map/pc.h  (revision 14435)
    +++ trunk/src/map/pc.h  (working copy)
    @@ -406,7 +406,7 @@


     //Update this max as necessary. 54 is the value needed for Super Baby currently
    -#define MAX_SKILL_TREE 54
    +#define MAX_SKILL_TREE 64 // 3rd Jobs
     //Total number of classes (for data storage)
     #define CLASS_COUNT (JOB_MAX - JOB_NOVICE_HIGH + JOB_MAX_BASIC)

    @@ -518,6 +518,9 @@
     #define pc_iscarton(sd)       ( (sd)->sc.option&OPTION_CART )
     #define pc_isfalcon(sd)       ( (sd)->sc.option&OPTION_FALCON )
     #define pc_isriding(sd)       ( (sd)->sc.option&OPTION_RIDING )
    +#define pc_isridingdragon(sd) ( (sd)->sc.option&OPTION_RIDING_DRAGON )
    +#define pc_iswarg(sd)        ( (sd)->sc.option&OPTION_WARG )
    +#define pc_isridingwarg(sd)   ( (sd)->sc.option&OPTION_RIDING_WARG )
     #define pc_isinvisible(sd)    ( (sd)->sc.option&OPTION_INVISIBLE )
     #define pc_is50overweight(sd) ( (sd)->weight*100 >= (sd)->max_weight*battle_config.natural_heal_weight_rate )
     #define pc_is90overweight(sd) ( (sd)->weight*10 >= (sd)->max_weight*9 )
    @@ -530,7 +533,7 @@
     #define pc_check_weapontype(sd, type) ((type)&((sd)->status.weapon < MAX_WEAPON_TYPE? \
        1<<(sd)->status.weapon:(1<<(sd)->weapontype1)|(1<<(sd)->weapontype2)))
     //Checks if the given class value corresponds to a player class. [Skotlex]
    -#define pcdb_checkid(class_) (class_ < JOB_MAX_BASIC || (class_ >= JOB_NOVICE_HIGH && class_ < JOB_MAX))
    +#define pcdb_checkid(class_) (class_ < JOB_MAX_BASIC || (class_ >= JOB_NOVICE_HIGH && class_ <= JOB_SOUL_LINKER) || (class_ >= JOB_RUNE_KNIGHT && class_ < JOB_MAX ))

     int pc_class2idx(int class_);
     int pc_isGM(struct map_session_data *sd);
    Index: trunk/src/map/map.h
    ===================================================================
    --- trunk/src/map/map.h (revision 14435)
    +++ trunk/src/map/map.h (working copy)
    @@ -40,7 +40,7 @@
     #define NATURAL_HEAL_INTERVAL 500
     #define MIN_FLOORITEM 2
     #define MAX_FLOORITEM START_ACCOUNT_NUM
    -#define MAX_LEVEL 99
    +#define MAX_LEVEL 150
     #define MAX_DROP_PER_MAP 48
     #define MAX_IGNORE_LIST 20 // official is 14
     #define MAX_VENDING 12
    @@ -59,6 +59,9 @@
     #define JOBL_2_1 0x100 //256
     #define JOBL_2_2 0x200 //512
     #define JOBL_2 0x300
    +#define JOBL_3_1 0x400
    +#define JOBL_3_2 0x800
    +#define JOBL_3 0xC00

     #define JOBL_UPPER 0x1000 //4096
     #define JOBL_BABY 0x2000  //8192
    @@ -148,6 +151,34 @@
        MAPID_BABY_ALCHEMIST,
        MAPID_BABY_ROGUE,
        MAPID_BABY_SOUL_LINKER,
    +//3_1 classes
    +   MAPID_RUNE_KNIGHT = JOBL_3_1|JOBL_2_1|0x1,
    +   MAPID_WARLOCK,
    +   MAPID_RANGER,
    +   MAPID_ARCHBISHOP,
    +   MAPID_MECHANIC,
    +   MAPID_GUILLOTINE_CROSS,
    +//3_1 advanced
    +   MAPID_RUNE_KNIGHT_H = JOBL_UPPER|JOBL_3_1|JOBL_2_1|0x1,
    +   MAPID_WARLOCK_H,
    +   MAPID_RANGER_H,
    +   MAPID_ARCHBISHOP_H,
    +   MAPID_MECHANIC_H,
    +   MAPID_GUILLOTINE_CROSS_H,
    +//3_2 classes
    +   MAPID_ROYAL_GUARD = JOBL_3_2|JOBL_2_2|0x1,
    +   MAPID_SORCERER,
    +   MAPID_MINSTRELWANDERER,
    +   MAPID_SHURA,
    +   MAPID_GENETIC,
    +   MAPID_SHADOW_CHASER,
    +//3_2 advanced
    +   MAPID_ROYAL_GUARD_H = JOBL_UPPER|JOBL_3_2|JOBL_2_2|0x1,
    +   MAPID_SORCERER_H,
    +   MAPID_MINSTRELWANDERER_H,
    +   MAPID_SHURA_H,
    +   MAPID_GENETIC_H,
    +   MAPID_SHADOW_CHASER_H,
     };

     //Max size for inputs to Graffiti, Talkie Box and Vending text prompts

Configuration
-------------

    Index: trunk/conf/msg_athena.conf
    ===================================================================
    --- trunk/conf/msg_athena.conf  (revision 14435)
    +++ trunk/conf/msg_athena.conf  (working copy)
    @@ -540,8 +540,39 @@
     619: Gunslinger
     620: Ninja
     621: Summer
    -//...
    -650: Unknown Job
    +622: Rune Knight
    +623: Warlock
    +624: Ranger
    +625: Arch Bishop
    +626: Mechanic
    +627: Guillotine Cross
    +628: Rune Knight
    +629: Warlock
    +630: Ranger
    +631: Arch Bishop
    +632: Mechanic
    +633: Guillotine Cross
    +634: Royal Guard
    +635: Sorcerer
    +636: Minstrel
    +637: Wanderer
    +638: Shura
    +639: Genetic
    +640: Shadow Chaser
    +641: Royal Guard
    +642: Sorcerer
    +643: Minstrel
    +644: Wanderer
    +645: Shura
    +646: Genetic
    +647: Shadow Chaser
    +648: Rune Knight Dragon
    +649: Rune Knight Dragon
    +650: Royal Guard Gryphon
    +651: Royal Guard Gryphon
    +652: Ranger Warg
    +653: Ranger Warg
    +654: Unknown Job

     //Custom translations
     import: conf/import/msg_conf.txt

DB
--

    Index: trunk/db/exp.txt
    ===================================================================
    --- trunk/db/exp.txt    (revision 14435)
    +++ trunk/db/exp.txt    (working copy)
    @@ -22,3 +22,11 @@
     50,4047:4048,1,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,27434,54868,70216,77154,84412,105416,133942,165376,179088,193338,235642,289842,348402,373354,399168,477234,572732,674294,716870,760752,895370,1053978,1220492,1289472,1587070,1843620,2213516,2521910,2974608,3115314,3981264,4166772
     //Job - Ninja/Gunslinger
     70,24:25,1,72,92,142,174,301,443,548,799,1270,1838,2145,2473,3339,4746,6385,7172,8002,10321,13717,17554,19288,21103,26354,33485,41344,44772,48334,58910,72460,87100,93338,99792,119308,143183,231068,257377,274363,314246,371105,431038,476309,588548,665256,801731,916689,1130023,1188623,1477408,1551289,1746582,1845236,1954741,2124555,2345698,2548763,2759555,3021488,3254111,3489547,3695474,4012251,4181112,4302211,4496584,4578951,4869523,5022114,5123654,5395117
    +//Base - Normal Renewal
    +150,4053:4054:4055:4056:4057:4058:4059:4066:4067:4068:4069:4070:4071:4072:4080:4082:4084,0,9,16,25,36,77,112,153,200,253,320,385,490,585,700,830,970,1120,1260,1420,1620,1860,1990,2240,2504,2950,3426,3934,4474,6889,7995,9174,10425,11748,13967,15775,17678,19677,21773,30543,34212,38065,42102,46323,53026,58419,64041,69892,75973,102468,115254,128692,142784,157528,178184,196300,215198,234879,255341,330188,365914,403224,442116,482590,536948,585191,635278,687211,740988,925400,1473746,1594058,1718928,1848355,1982340,2230113,2386162,2547417,2713878,3206160,3681024,4022472,4377024,4744680,5125440,5767272,6204000,6655464,7121664,7602600,9738720,11649960,13643520,18339300,23836800,35658000,48687000,58135000,99999999
    +//Job - Normal Renewal
    +50,4053:4054:4055:4056:4057:4058:4059:4066:4067:4068:4069:4070:4071:4072:4080:4082:4084,1,144,184,284,348,603,887,1096,1598,2540,3676,4290,4946,6679,9492,12770,14344,16005,20642,27434,35108,38577,42206,52708,66971,82688,89544,96669,117821,144921,174201,186677,199584,238617,286366,337147,358435,380376,447685,526989,610246,644736,793535,921810,1106758,1260955,1487304,1557657,1990632,2083386
    +//Base - Adv Renewal
    +150,4060:4061:4062:4063:4064:4065:4073:4074:4075:4076:4077:4078:4079:4081:4083:4085,0,10,18,28,40,85,123,168,220,278,400,481,613,731,875,1038,1213,1400,1575,1775,2268,2604,2786,3136,3506,4130,4796,5508,6264,9645,12392,14220,16159,18209,21649,24451,27401,30499,33748,47342,58160,64711,71573,78749,90144,99312,108870,118816,129154,174196,213220,238080,264150,291427,329640,363155,398116,434526,472381,610848,731828,806448,884232,965180,1073896,1170382,1270556,1374422,1481976,1850800,3389616,3666333,3953534,4251217,4559382,5129260,5488173,5859059,6241919,7374168,9570662,10458427,11380262,12336168,13326144,14994907,16130400,17304200,18516326,19766760,29216160,34949880,40930560,55017900,71510400,106974000,146061000,174405000,343210000
    +//Job - Adv Renewal
    +70,4060:4061:4062:4063:4064:4065:4073:4074:4075:4076:4077:4078:4079:4081:4083:4085,1,288,368,568,696,1206,1774,2192,3196,5080,7352,8580,9892,13358,18984,31925,35860,40013,51605,68585,87770,96443,105515,131770,167428,206720,223860,241673,294553,362303,479053,513362,548856,656197,787507,927154,985696,1046034,1231134,1449220,1678177,1773024,2182221,2534978,3043585,3782865,4461912,4672971,5971896,6250158,6875174,7562691,8318960,9150856,10065942,11877812,14015818,16538655,19515624,23028437,28094693,34275525,41816141,51015692,62239144,79666104,101972614,130524946,167071930,213852071
    Index: trunk/db/job_db1.txt
    ===================================================================
    --- trunk/db/job_db1.txt    (revision 14435)
    +++ trunk/db/job_db1.txt    (working copy)
    @@ -153,3 +153,67 @@
     4048, 28000,90   ,650  ,470  ,400  ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,500  ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
     // Soul Linker
     4049, 24000,75   ,500  ,900  ,500  ,575  ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,625  ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 625
    +// Rune Knight
    +4054, 29000,150 ,500 ,300 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Warlock
    +4055, 25000,55 ,500 ,900 ,500 ,575 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,625 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 625
    +// Ranger
    +4056, 28000,85 ,500 ,400 ,400 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Arch Bishop
    +4057, 27000,75 ,500 ,800 ,400 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,600 ,600 ,600 ,2000 ,2000 ,2000 ,2000 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 600
    +// Mechanic
    +4058, 31000,90 ,500 ,400 ,400 ,600 ,650 ,2000 ,2000 ,2000 ,650 ,650 ,675 ,675 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Guillotine Cross
    +4059, 25000,110 ,500 ,400 ,400 ,500 ,650 ,2000 ,2000 ,2000 ,800 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,500 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Rune Knight T
    +4060, 29100,150 ,500 ,300 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Warlock T
    +4061, 25100,55 ,500 ,900 ,500 ,575 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,625 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 625
    +// Ranger T
    +4062, 28100,85 ,500 ,400 ,400 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Arch Bishop T
    +4063, 27100,75 ,500 ,800 ,400 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,600 ,600 ,600 ,2000 ,2000 ,2000 ,2000 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 600
    +// Mechanic T
    +4064, 31100,90 ,500 ,400 ,400 ,600 ,650 ,2000 ,2000 ,2000 ,650 ,650 ,675 ,675 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Guillotine Cross T
    +4065, 25100,110 ,500 ,400 ,400 ,500 ,650 ,2000 ,2000 ,2000 ,800 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,500 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Royal Guard
    +4066, 29000,110 ,700 ,470 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Sorcerer
    +4067, 25000,75 ,500 ,700 ,450 ,525 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,625 ,2000 ,2000 ,2000 ,2000 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 625
    +// Minstrel
    +4068, 28000,75 ,300 ,600 ,400 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,650 ,2000 ,575 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Wanderer
    +4069, 28000,75 ,300 ,600 ,400 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,650 ,2000 ,2000 ,575 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Shura
    +4070, 27000,90 ,650 ,470 ,400 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,575 ,575 ,575 ,2000 ,475 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 575
    +// Genetic
    +4071, 31000,90 ,500 ,400 ,400 ,550 ,575 ,2000 ,2000 ,2000 ,675 ,700 ,650 ,650 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Dark Chaser
    +4072, 25000,85 ,500 ,500 ,400 ,500 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,650 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Royal Guard H
    +4073, 29100,110 ,700 ,470 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Sorcerer H
    +4074, 25100,75 ,500 ,700 ,450 ,525 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,625 ,2000 ,2000 ,2000 ,2000 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 625
    +// Minstrel H
    +4075, 28100,75 ,300 ,600 ,400 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,650 ,2000 ,575 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Wanderer H
    +4076, 28100,75 ,300 ,600 ,400 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,650 ,2000 ,2000 ,575 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Shura H
    +4077, 27100,90 ,650 ,470 ,400 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,575 ,575 ,575 ,2000 ,475 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 , 575
    +// Genetic H
    +4078, 31100,90 ,500 ,400 ,400 ,550 ,575 ,2000 ,2000 ,2000 ,675 ,700 ,650 ,650 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Dark Chaser H
    +4079, 25100,85 ,500 ,500 ,400 ,500 ,550 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,650 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Rune Knight (Peko)
    +4080, 29000,150 ,500 ,300 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Rune Knight H (Peko)
    +4081, 29100,150 ,500 ,300 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Royal Guard (Peko)
    +4082, 29000,110 ,700 ,470 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Royal Guard H (Peko)
    +4083, 29100,110 ,700 ,470 ,400 ,500 ,500 ,550 ,600 ,600 ,700 ,700 ,650 ,700 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Ranger (Wolf)
    +4084, 28000,85 ,500 ,400 ,400 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    +// Ranger H (Wolf)
    +4085, 28100,85 ,500 ,400 ,400 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,600 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000 ,2000
    Index: trunk/db/job_db2.txt
    ===================================================================
    --- trunk/db/job_db2.txt    (revision 14435)
    +++ trunk/db/job_db2.txt    (working copy)
    @@ -161,3 +161,67 @@
     4048,1,1,1,1,1,1,1,1,1,1,1,1,0,0,0,0,0,0,0,5,5,5,5,5,5,0,0,0,0,0,0,0,0,0,0,0,0,0,2,2,2,2,2,2,2,2,2,2,2,2
     // Soul Linker
     4049,4,4,4,4,4,4,4,4,4,4,4,4,0,0,0,0,0,0,0,3,3,3,3,3,3,0,0,0,0,0,0,0,0,0,0,0,0,0,5,5,5,5,5,5,5,5,5,5,5,5
    +// Rune Knight
    +4054,3,0,3,1,6,0,0,3,0,1,5,3,2,0,1,0,3,3,5,6,1,0,3,0,0,0,1,6,3,0,5,0,1,0,0,3,0,2,0,5,0,0,3,0,0,1,1,5,5,0,5,0,1,0,0,3,6,2,0,5,0,0,3,0,0,1,1,5,5,0
    +// Warlock
    +4055,4,5,0,4,5,2,0,0,4,2,0,1,5,0,6,0,0,4,0,0,0,4,0,2,0,5,0,0,4,0,4,5,4,2,0,6,0,3,5,4,2,0,2,0,4,2,2,4,0,4,4,5,4,2,0,6,0,3,5,4,2,0,2,0,4,2,2,4,0,4
    +// Ranger
    +4056,5,0,4,5,1,0,6,5,0,1,1,2,0,5,6,0,3,0,2,2,5,3,0,0,0,0,5,0,6,0,2,0,5,4,0,0,0,5,2,0,4,6,5,1,0,4,2,0,5,0,2,0,5,4,0,0,0,5,2,0,4,6,5,1,0,4,2,0,5,0
    +// Arch Bishop
    +4057,6,0,6,1,0,2,3,4,4,6,1,0,0,3,5,0,1,0,0,5,6,4,0,0,5,0,1,0,2,0,6,5,0,3,1,3,0,0,6,0,0,4,4,0,3,0,0,2,0,6,6,5,0,3,1,3,2,0,6,0,0,4,4,0,3,0,0,2,0,6
    +// Mechanic
    +4058,5,0,1,5,5,0,3,1,0,5,6,5,3,0,0,1,0,0,5,3,4,0,1,0,0,5,0,5,2,0,1,3,0,4,0,5,0,2,5,5,0,0,0,1,0,6,5,0,3,0,1,3,0,4,0,5,3,2,5,5,0,0,0,1,0,6,5,0,3,0
    +// Guillotine Cross
    +4059,2,2,2,4,0,3,0,3,5,0,1,0,0,4,2,2,2,2,2,2,2,0,0,5,1,0,1,0,0,5,5,1,0,0,0,0,0,4,0,5,5,4,0,0,1,5,0,1,0,5,5,1,0,0,0,0,0,4,0,5,5,4,0,0,1,5,0,1,0,5
    +// Rune Knight H
    +4060,1,2,6,5,3,1,1,1,0,2,5,3,4,2,0,5,2,0,1,0,0,3,0,0,1,0,6,5,3,0,5,0,1,0,0,5,0,6,0,3,1,0,3,5,0,1,1,0,5,0,0,1,2,0,0,1,1,3,0,2,0,5,0,1,2,0,4,3,0,1,0,1,2,0,0,1,1,3,0,2,0,5,0,1,2,0,4,3,0,1
    +// Warlock H
    +4061,4,5,3,0,4,0,0,2,5,4,0,6,0,4,0,0,5,2,4,1,0,5,5,4,0,2,0,4,3,0,5,4,0,2,0,0,0,4,4,1,6,0,5,0,0,4,3,0,4,2,0,0,3,0,4,2,6,0,4,1,5,4,0,0,2,3,5,0,2,4,0,0,3,0,4,2,6,0,0,1,5,4,0,0,2,3,5,0,2,4
    +// Ranger H
    +4062,5,2,5,5,4,2,0,1,0,2,2,3,0,6,0,5,5,0,0,4,2,5,0,1,6,5,0,2,0,5,6,3,2,0,5,6,0,2,0,5,0,4,2,0,1,5,0,2,0,6,5,0,0,4,3,0,6,2,0,5,1,6,0,0,4,0,0,0,5,6,5,0,0,4,3,0,6,2,0,5,1,6,0,0,4,0,0,0,5,6
    +// Arch Bishop H
    +4063,4,0,2,3,1,0,4,2,0,0,4,1,5,0,0,5,0,0,2,4,1,3,4,4,0,5,0,5,2,3,1,0,0,4,0,0,0,1,0,6,0,2,5,0,1,5,4,0,6,3,3,0,0,0,2,5,4,3,0,1,4,5,0,0,2,4,3,2,0,4,3,0,0,0,2,5,4,3,0,1,4,5,0,0,2,4,3,2,0,4
    +// Mechanic H
    +4064,5,1,1,4,0,5,2,6,3,0,0,5,3,0,4,6,1,0,2,2,0,4,5,0,0,1,0,6,3,0,2,5,1,4,0,2,0,5,6,0,5,0,0,6,6,0,5,3,0,4,0,1,0,0,5,5,0,2,0,3,4,5,0,2,3,6,6,0,0,5,3,0,0,0,2,5,4,3,0,1,4,5,0,0,2,4,3,2,0,4
    +// Guillotine Cross H
    +4065,2,1,6,2,2,0,1,6,3,5,0,1,0,0,2,6,0,6,0,2,1,0,5,2,2,6,0,0,1,0,2,2,2,6,0,0,0,1,5,0,0,2,5,0,0,2,3,6,0,1,2,0,5,1,0,2,5,0,0,0,5,2,0,5,6,1,0,0,3,5,2,0,5,1,0,2,5,0,0,0,5,2,0,5,6,1,0,0,3,5
    +// Royal Guard
    +4066,6,6,6,6,6,0,1,0,4,0,1,3,0,5,3,0,1,0,0,4,4,3,1,0,1,0,0,5,0,2,0,1,0,5,4,2,0,4,0,3,3,0,0,4,0,3,0,1,0,3,0,1,0,5,4,2,0,4,0,3,3,0,0,4,0,3,0,1,0,3
    +// Sorcerer
    +4067,4,0,2,3,0,2,0,4,0,0,3,0,2,0,4,0,6,3,0,5,0,2,0,4,5,0,5,0,0,4,0,5,2,0,6,0,0,4,5,6,0,1,0,1,4,1,1,1,0,4,0,5,2,0,6,0,4,4,5,6,0,1,0,1,4,1,1,1,0,4
    +// Minstrel
    +4068,5,2,1,0,4,6,5,0,6,2,2,0,4,0,5,5,3,0,5,6,4,0,0,2,0,0,0,1,0,2,0,5,3,0,2,0,0,5,0,4,6,0,3,0,0,5,4,2,0,5,0,5,3,0,2,0,0,5,0,4,6,0,3,0,0,5,4,2,0,5
    +// Wanderer
    +4069,6,2,1,0,4,5,6,0,5,2,2,0,4,0,6,5,3,0,6,5,4,0,0,2,0,0,0,1,0,2,0,6,3,0,2,0,0,6,0,4,5,0,3,0,0,6,4,2,0,6,0,6,3,0,2,0,0,6,0,4,5,0,3,0,0,6,4,2,0,6
    +// Shura
    +4070,1,1,0,5,2,0,3,0,0,2,0,1,1,0,6,4,0,2,0,3,2,5,2,0,3,1,1,0,0,5,0,6,3,0,2,0,0,4,0,6,3,0,5,2,0,3,0,0,1,1,0,6,3,0,2,0,0,4,0,6,3,0,5,2,0,3,0,0,1,1
    +// Genetic
    +4071,4,5,5,0,0,1,0,5,4,0,2,0,5,2,1,0,4,0,5,3,5,0,4,4,5,1,0,5,4,0,3,5,0,1,0,3,0,4,0,2,0,0,1,0,2,0,0,0,2,2,3,5,0,1,0,3,0,4,0,2,0,0,1,0,2,0,0,0,2,2
    +// Dark Chaser
    +4072,2,3,5,0,1,3,2,0,3,0,5,0,0,3,3,2,0,5,0,5,0,0,2,0,1,3,1,0,2,1,0,0,5,5,0,1,0,4,2,0,0,1,4,0,2,0,4,4,0,5,0,0,5,5,0,1,0,4,2,0,0,1,4,0,2,0,4,4,0,5
    +// Royal Guard H
    +4073,3,1,2,0,0,5,4,2,3,1,0,5,0,4,3,2,5,1,0,0,3,0,5,2,0,1,0,0,4,3,0,0,1,0,0,5,0,0,6,1,0,3,4,0,5,0,0,1,3,0,0,2,3,4,1,0,5,0,6,2,4,0,3,1,4,0,6,5,3,2,0,2,3,4,1,0,5,0,0,2,4,0,3,1,4,0,6,5,3,2
    +// Sorcerer H
    +4074,4,4,2,0,1,0,3,5,0,0,4,2,0,4,0,5,0,1,0,5,6,4,2,3,0,5,1,0,5,4,0,2,0,5,0,1,0,4,3,0,4,0,2,0,1,5,0,0,4,2,0,5,0,2,5,1,4,0,0,2,0,5,3,4,0,6,0,4,2,4,0,5,0,2,5,1,4,0,0,2,0,5,3,4,0,6,0,4,2,4
    +// Minstrel H
    +4075,2,5,0,2,1,0,5,4,2,1,6,0,2,0,5,3,0,6,1,0,4,0,5,2,0,6,0,4,0,5,0,2,1,0,0,2,0,0,5,5,4,0,5,0,1,0,6,0,2,5,0,0,2,1,0,5,5,2,3,0,5,1,5,0,2,5,0,2,4,1,0,0,2,1,0,5,5,2,0,0,5,1,5,0,2,5,0,2,4,1
    +// Wanderer H
    +4076,5,1,0,2,0,1,0,4,5,0,2,2,2,5,5,0,3,5,0,1,0,0,5,5,2,4,6,5,0,0,2,0,5,0,1,0,0,2,4,0,5,0,5,0,5,0,2,0,5,1,0,2,4,3,0,0,2,5,0,4,2,2,6,0,5,1,2,0,5,2,0,2,4,3,0,0,2,5,0,4,2,2,6,0,5,1,2,0,5,2
    +// Shura H
    +4077,1,4,3,2,0,5,0,0,1,0,4,2,6,0,3,5,1,0,0,2,2,5,0,3,0,0,1,0,2,5,0,0,4,6,0,0,0,5,3,0,0,3,0,5,2,6,4,1,0,5,0,2,5,0,0,4,0,3,1,5,0,2,0,4,1,1,5,3,4,2,0,2,5,0,0,4,0,3,0,5,0,2,0,4,1,1,5,3,4,2
    +// Genetic H
    +4078,5,0,6,0,2,1,4,6,3,5,0,0,4,0,5,0,0,2,0,6,0,4,5,0,6,0,2,0,0,4,1,0,3,6,5,0,0,2,0,0,5,5,5,0,6,4,5,0,5,0,6,6,1,2,0,5,5,0,4,6,3,0,5,6,0,1,2,4,6,5,6,6,1,2,0,5,5,0,0,6,3,0,5,6,0,1,2,4,6,5
    +// Dark Chaser H
    +4079,1,2,0,6,4,3,0,0,2,5,1,2,0,0,3,5,5,0,0,6,2,1,0,6,0,5,2,0,5,0,6,1,0,2,0,0,0,5,0,0,2,3,1,4,2,0,1,0,5,6,0,5,1,0,0,5,4,2,6,5,0,1,3,2,0,5,1,0,0,2,0,5,1,0,0,5,4,2,0,5,0,1,3,2,0,5,1,0,0,2
    +// Rune Knight (Peko)
    +4080,3,0,3,1,6,0,0,3,0,1,5,3,2,0,1,0,3,3,5,6,1,0,3,0,0,0,1,6,3,0,5,0,1,0,0,3,0,2,0,5,0,0,3,0,0,1,1,5,5,0,5,0,1,0,0,3,6,2,0,5,0,0,3,0,0,1,1,5,5,0
    +// Rune Knight H (Peko)
    +4081,1,2,6,5,3,1,1,1,0,2,5,3,4,2,0,5,2,0,1,0,0,3,0,0,1,0,6,5,3,0,5,0,1,0,0,5,0,6,0,3,1,0,3,5,0,1,1,0,5,0,0,1,2,0,0,1,1,3,0,2,0,5,0,1,2,0,4,3,0,1,0,1,2,0,0,1,1,3,0,2,0,5,0,1,2,0,4,3,0,1
    +// Royal Guard (Peko)
    +4082,6,6,6,6,6,0,1,0,4,0,1,3,0,5,3,0,1,0,0,4,4,3,1,0,1,0,0,5,0,2,0,1,0,5,4,2,0,4,0,3,3,0,0,4,0,3,0,1,0,3,0,1,0,5,4,2,0,4,0,3,3,0,0,4,0,3,0,1,0,3
    +// Royal Guard H (Peko)
    +4083,3,1,2,0,0,5,4,2,3,1,0,5,0,4,3,2,5,1,0,0,3,0,5,2,0,1,0,0,4,3,0,0,1,0,0,5,0,0,6,1,0,3,4,0,5,0,0,1,3,0,0,2,3,4,1,0,5,0,6,2,4,0,3,1,4,0,6,5,3,2,0,2,3,4,1,0,5,0,0,2,4,0,3,1,4,0,6,5,3,2
    +// Ranger (Wolf)
    +4084,5,0,4,5,1,0,6,5,0,1,1,2,0,5,6,0,3,0,2,2,5,3,0,0,0,0,5,0,6,0,2,0,5,4,0,0,0,5,2,0,4,6,5,1,0,4,2,0,5,0,2,0,5,4,0,0,0,5,2,0,4,6,5,1,0,4,2,0,5,0
    +// Ranger H (Wolf)
    +4085,5,2,5,5,4,2,0,1,0,2,2,3,0,6,0,5,5,0,0,4,2,5,0,1,6,5,0,2,0,5,6,3,2,0,5,6,0,2,0,5,0,4,2,0,1,5,0,2,0,6,5,0,0,4,3,0,6,2,0,5,1,6,0,0,4,0,0,0,5,6,5,0,0,4,3,0,6,2,0,5,1,6,0,0,4,0,0,0,5,6
    Index: trunk/db/const.txt
    ===================================================================
    --- trunk/db/const.txt  (revision 14435)
    +++ trunk/db/const.txt  (working copy)
    @@ -80,9 +80,45 @@
     Job_Star_Gladiator2    4048
     Job_Soul_Linker    4049

    +Job_Rune_Knight 4054
    +Job_Warlock    4055
    +Job_Ranger     4056
    +Job_Arch_Bishop 4057
    +Job_Mechanic   4058
    +Job_Guillotine_Cross   4059
    +Job_Rune_Knight_H  4060
    +Job_Warlock_H  4061
    +Job_Ranger_H   4062
    +Job_Arch_Bishop_H  4063
    +Job_Mechanic_H     4064
    +Job_Guillotine_Cross_H     4065
    +Job_Royal_Guard    4066
    +Job_Sorcerer   4067
    +Job_Minstrel   4068
    +Job_Wanderer   4069
    +Job_Shura  4070
    +Job_Genetic    4071
    +Job_Shadow_Chaser  4072
    +Job_Royal_Guard_H  4073
    +Job_Sorcerer_H     4074
    +Job_Minstrel_H     4075
    +Job_Wanderer_H     4076
    +Job_Shura_H    4077
    +Job_Genetic_H  4078
    +Job_Shadow_Chaser_H    4079
    +Job_Rune_Knight2   4080
    +Job_Rune_Knight2_H     4081
    +Job_Royal_Guard2   4082
    +Job_Royal_Guard2_H     4083
    +Job_Ranger2    4084
    +Job_Ranger2_H  4085
    +
     EAJL_2_1   0x100
     EAJL_2_2   0x200
     EAJL_2 0x300
    +EAJL_3_1   0x400
    +EAJL_3_2   0x800
    +EAJL_3     0xC00
     EAJL_UPPER 0x1000
     EAJL_BABY  0x2000
     EAJ_UPPERMASK  0x0fff
    @@ -164,6 +200,34 @@
     EAJ_BABY_ROGUE 0x2206
     EAJ_BABY_SOUL_LINKER   0x2207

    +EAJ_RUNE_KNIGHT    0x501
    +EAJ_WARLOCK    0x502
    +EAJ_RANGER     0x503
    +EAJ_ARCH_BISHOP    0x504
    +EAJ_MECHANIC   0x505
    +EAJ_GUILLOTINE_CROSS   0x506
    +
    +EAJ_RUNE_KNIGHT_H  0x1501
    +EAJ_WARLOCK_H  0x1502
    +EAJ_RANGER_H   0x1503
    +EAJ_ARCH_BISHOP_H  0x1504
    +EAJ_MECHANIC_H     0x1505
    +EAJ_GUILLOTINE_CROSS_H     0x1506
    +
    +EAJ_ROYAL_GUARD    0xA01
    +EAJ_SORCERER   0xA02
    +EAJ_MINSTRELWANDERER   0xA03
    +EAJ_SHURA  0xA04
    +EAJ_GENETIC    0xA05
    +EAJ_SHADOW_CHASER  0xA06
    +
    +EAJ_ROYAL_GUARD_H  0x1A01
    +EAJ_SORCERER_H     0x1A02
    +EAJ_MINSTRELWANDERER_H     0x1A03
    +EAJ_SHURA_H    0x1A04
    +EAJ_GENETIC_H  0x1A05
    +EAJ_SHADOW_CHASER_H    0x1A06
    +
     Option_Wedding 0x1000
     Option_Xmas    0x10000
     Option_Summer  0x40000

**Note:** Levels 100-150 in db/exp.txt are not part of the diff.

Client Side
-----------

[for the ready made sprites - Click here](http://www.eathena.ws/board/index.php?showtopic=217782)

get rdata.grf [HERE](ftp://ragadmin:icsragadmin!%40@ragnarok1-gravity.ktics.co.kr/RAGRE_SETUP0325.exe) and merge the palette folder to your grf/data folder you will be using it for the 3rd jobs palettes

[Category:Customization](/Category:Customization "wikilink") [Category:Source Snippets](/Category:Source_Snippets "wikilink")