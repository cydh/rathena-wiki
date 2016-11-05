---
title: Packet DB Rewrite
permalink: /Packet_DB_Rewrite/
---

Motivation
==========

Right now, the basic information about packets is stored in at least two different places. This is undesirable in many aspects, not the least of which being hard maintenance. Furthermore, the custom(?) system in place by the name of **packet_ver** has probably not been operating as intended for a long time, and thus may mislead users.

Proposed Changes
================

Abolish packet_ver
-------------------

*Way back*, **packet_ver** served to allow a server to handle multiple client versions at the same time, identifying them by their WantToConnection packet. Thus, with each such packet, a new **packet_ver** version was added. Since the server, however, also relies on a hardcoded compile time define called **PACKETVER** in many places, the chances of the mechanism still working as intended are slim to none. Especially nowadays, servers will most likely only ever be concerned with only one client type, and the setting should be safe to drop, along with all related code(like identifying the **packet_ver** of a client on connecting).

Remove the hardcoded values for packet_lens in clif.c
------------------------------------------------------

The idea here is simply centralization. All of values could simply be stored in packet_db with the respective client date.

Index packet_db by client date
-------------------------------

A new format would be required for what right now is present in comment form above every set of new/changed packets. It would simply contain the client date (as corresponds to **PACKETVER**. When building the packet_len array on map server start-up, the server would then simply accumulative all changes from the first version to the value of **PACKETVER**, overwriting as it goes, and stopping after reaching the corresponding date.