# Quest Loading

## How Quests Are Loaded:

## NPC

In order of operations, an npc's script will be dictated by the first script that it finds below.  The \[ext\] refers to file extension--either .pl or .lua.  It should be noted that a .lua file takes precedence over a .pl file of the same name. 

These scripts run in a context based on NPCID.  All npcs with the same NPCID can see variables, modify them, and see changes made by the others.  If you need variables that are specific to each instance of an NPCID, data buckets or entity variables can be used.

| Hierarchy | Example |
| :--- | :--- |
| quests/zoneshortname/id.\[ext\] | quests/qeynos/1173.lua |
| quests/zoneshortname/npc\_name.\[ext\] | quests/qeynos/Trumpy\_Irontoe.pl |
| quests/global/npcid.\[ext\] | quests/global/1234.pl |
| quests/global/npc\_name.\[ext\] | quests/global/Nexus\_Scion.lua |
| quests/zoneshortname/default.\[ext\] | quests/tutorialb/default.pl |
| quests/global/default.\[ext\] | quests/global/default.lua |

## Player

In order of operations, a player's script will be dictated by the first script that it finds below.  The \[ext\] refers to file extension--either .pl or .lua.  It should be noted that a .lua file takes precedence over a .pl file of the same name. 

| Hierarchy | Example |
| :--- | :--- |
| quests/zoneshortname/player\_v\[instance\_version\].\[ext\] | quests/qeynos/player\_v1.pl |
| quests/zoneshortname/player.\[ext\] | quests/qeynos/player.lua |
| quests/global/player.\[ext\] | quests/global/player.pl |

## Global Scripts

Global scripts were designed to run on top of the scripts mentioned above, meaning if you have a player script in a zone directory and a global player script, they will both execute and not interfere with each other

#### Player

* quests/global/global\_player.ext

#### NPC

* quests/global/global\_npc.ext

The global\_npc.ext scripts run in a zone wide context.  All npcs in the same zone can see variables, modify them, and see changes made by the others.

## Item

Item Scripts are quest scripts attached to Items. Items will load a script on the first event that triggers them and will load one and only one from the following location. Which ever it finds first in the following order:

| Hierarchy | Example |
| :--- | :--- |
| quests/zone/items/item\_script.\[ext\] | quests/qeynos/items/script\_30057.pl |
| quests/global/items/item\_script.\[ext\] | quests/global/items/script\_30057.lua |
| quests/zone/items/default.\[ext\] | quests/qeynos/items/default.lua |
| quests/global/items/default.\[ext\] | quests/global/items/default.pl |

## Spell Scripts

Spell Scripts are quest scripts attached to Spells. Spells will load a script on the first event that triggers them and will load one and only one from the following location. Which ever it finds first in the following order:

| Hierarchy | Example |
| :--- | :--- |
| quests/zone/spells/spell\_id.\[ext\] | quests/qeynos/spells/1234.pl |
| quests/global/spells/spell\_id.\[ext\] | quests/global/spells/1234.lua |
| quests/zone/spells/default.\[ext\] | quests/qeynos/spells/default.lua |
| quests/global/spells/default.\[ext\] | quests/global/spells/default.pl |

