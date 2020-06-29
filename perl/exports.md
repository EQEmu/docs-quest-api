---
description: >-
  This is a list of the global exports during subroutines.  Some exported
  variables are only available in certain sub routines. See the Events page for
  a listing of each event and corresponding exports.
---

# Exports

### ProTip: hit ctrl + f \(Windows\) or ⌘ + f \(Mac\) to FIND something on this page

A full list can always be found in the EQEmu source [https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp](https://github.com/EQEmu/Server/blob/master/zone/embparser.cpp)

| Exported Variable | Usage |
| :--- | :--- |
| $activity\_id | Returns the ID of the task stage completed \(in EVENT\_TASK\_STAGE\_COMPLETE\); Returns the ID of the task updated or complete \(in EVENT\_TASK\_COMPLETE, EVENT\_TASK\_UPDATE\) |
| $charid | Returns the character ID of the client that triggered the Event or a negative value if no client was involved. |
| $class | Returns the class of the user that triggered the event. |
| $caster\_id | Returns the ID of the caster \(in EVENT\_SPELL\_EFFECT\_CLIENT, EVENT\_SPELL\_EFFECT\_NPC, EVENT\_SPELL\_BUFF\_TIC\_CLIENT, EVENT\_SPELL\_BUFF\_TIC\_NPC\) |
| $combat\_state | Returns 1 for starting combat, returns 0 for leaving combat \(in EVENT\_COMBAT\) |
| $corpse | Returns the ID of the corpse in which an item was looted \(in EVENT\_LOOT\) |
| $donecount | Return the number of hand-ins completed \[i.e. 5 of 10 Crushbone Belts, the 5 would be returned\] \(in EVENT\_TASK\_COMPLETE, EVENT\_TASK\_UPDATE\) |
| $doorid | Returns ID of the door clicked \(in EVENT\_CLICK\_DOOR\) |
| $faction | Returns the faction level number of the user with the NPC |
| $fished\_items | Returns the item ID of fished item \(in EVENT\_FISH\_SUCCESS\) |
| $foraged\_item | Returns the item ID of foraged item \(in EVENT\_FORAGE\_SUCCESS\) |
| $grouped | Returns 0 or 1 depending on group status \(in EVENT\_GROUP\_CHANGED\) |
| $hate\_state | Return the state of hate \(in EVENT\_HATE\_LIST\) |
| $hpevent | Returns the value set by quest::setnexthpevent\(\); |
| $item1 | The item ID in the first slot. |
| $item2 | The item ID in the second slot. |
| $item3 | The item ID in the third slot. |
| $item4 | The item ID in the fourth slot. |
| $item1\_charges | The number of charges in the first slot. |
| $item2\_charges | The number of charges in the second slot. |
| $item3\_charges | The number of charges in the third slot. |
| $item4\_charges | The number of charges in the fourth slot. |
| $item1\_attuned | The attuned setting in the first slot \(1 if attuned, 0 if not attuned\). |
| $item2\_attuned | The attuned setting in the second slot \(1 if attuned, 0 if not attuned\). |
| $item3\_attuned | The attuned setting in the third slot \(1 if attuned, 0 if not attuned\). |
| $item4\_attuned | The attuned setting in the fourth slot \(1 if attuned, 0 if not attuned\). |
| $itemcount{itemid} |  |
| $itemid | Return the item ID of items used \(in EVENT\_ITEM\_CLICK\_CAST, EVENT\_ITEM\_CLICK\) |
| $itemname | Returns the item name of items used \(in EVENT\_ITEM\_CLICK\_CAST, EVENT\_ITEM\_CLICK\) |
| $killed | Returns the NPC id of the npc slain \(in EVENT\_NPC\_SLAY\) |
| $killer\_damage | Returns the damage of the mob's killer's killing blow \(in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE\) |
| $killer\_id | Returns the entity ID of a mob's killer \(in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE\) |
| $killer\_skill | Returns the skill ID of the mob's killer's killing blow \(in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE\) |
| $killer\_spell | Returns the spell ID of the mob's killer's spell \(in EVENT\_DEATH, EVENT\_DEATH\_COMPLETE\) |
| $hasitem{itemid} | Checks the character's inventory master slots for an item |
| $hpevent | Used to identify the HP Event set via quest::setnexthpevent\(\) \(in EVENT\_HP\) |
| $hpratio | Returns HP Ratio |
| $inchpevent | Used potentially for the incoming hp event or next hp event \(in EVENT\_HP\) |
| $instanceid | Returns the instance ID of the current zone |
| $instanceversion | Returns the instance version |
| $langid | Returns the language id the player/npc is currently using. \(in EVENT\_SAY, EVENT\_AGGRO\_SAY, EVENT\_PROXIMITY\_SAY\) |
| $looted\_charges | Returns the charges of the looted item \(in EVENT\_LOOT\) |
| $looted\_id | Returns the ID of the looted item \(in EVENT\_LOOT\) |
| $oncursor{itemid} | Checks the character's front item on the cursor for an item |
| $objectid | Returns the object id of the clicked item \(in EVENT\_CLICK\_OBJECT\) |
| $mlevel | Returns the level of the mob that the user triggered the Event on. |
| $mname | Returns the mob's name \(returns non-clean, for a clean name use |
| $mobid | Returns the npc\_types ID of the mob that the user triggered the Event on. |
| $name | Returns the name of the user that triggered the Event. |
| $picked\_up\_id | Returns the item id picked up \(in EVENT\_PLAYER\_PICKUP\) |
| $popupid | Returns the ID of the popup window \(in EVENT\_POPUPRESPONSE\) |
| $race | Returns the race of the user that triggered the Event. |
| $raided | Returns 0 or 1 depending on group status \(in EVENT\_GROUP\_CHANGED\) |
| $recipe | Returns the ID of the recipe \(in EVENT\_COMBINE\_SUCCESS, EVENT\_COMBINE\_FAILURE\) |
| $signal | Returns the value of a signal sent using quest::signalwith\(\) \(in EVENT\_SIGNAL\) |
| $slotid | Returns the slot ID of the item used \(in EVENT\_ITEM\_CLICK\_CAST, EVENT\_ITEM\_CLICK\) |
| $spell\_id | Returns the ID of the spell cast \(in EVENT\_CAST, EVENT\_CAST\_ON, EVENT\_CAST\_BEGIN\) |
| $status | Returns the account status of the user that triggered the Event. |
| $target\_zone\_id | Returns the ID of the zone to enter, such as in casting ports \(in EVENT\_ZONE\) |
| $targetid | Returns the entity id of the NPC's current \(or last\) target. |
| $targetname | Returns the name of the NPC's current \(or last\) target. |
| $task\_id | Returns the task ID of the task accepted \(in EVENT\_TASKACCEPTED\), stage completed \(in EVENT\_TASK\_STAGE\_COMPLETE\), task failed \(in EVENT\_TASK\_FAIL\), task updated or completed \(in EVENT\_TASK\_COMPLETE, EVENT\_TASK\_UPDATE\) |
| $text | The text sent by players to an NPC \(in EVENT\_SAY\), from an NPC \(in EVENT\_AGGRO\_SAY\), spoken by player when nearby the NPC \(in EVENT\_PROXIMITY\_SAY\) |
| $timer | Returns the value used when creating a timer with quest::settimer\(\) \(in EVENT\_TIMER\) |
| $uguild\_id | Returns the ID of the guild of the user that triggered the Event. |
| $uguildrank | Returns the guild rank of the user that triggered the Event. |
| $ulevel | Returns the level of the user that triggered the Event. |
| $userid | Returns the ID of the user that triggered the Event. |
| $version | Returns the version of the door clicked \(in EVENT\_CLICKDOOR\) |
| $wp | Returns current waypoint \(in EVENT\_WAYPOINT\_ARRIVE and EVENT\_WAYPOINT\_DEPART\) |
| $zonehour | Returns the current in-game hour. |
| $zoneid | Returns the zone id that the Event occured in. |
| $zoneln | Returns the zone long name that the Event occured in. |
| $zonemin | Returns the current in-game minute. |
| $zonesn | Returns the zone short name that the Event occured in. |
| $zonetime | Returns the current in-game time in HHMM format. |
| $zoneweather | Returns current weather of zone. 0 for none, 1 for rain, 2 for snow. |
| $copper | Returns the number of copper coins given to the mob. |
| $silver | Returns the number of silver coins given to the mob. |
| $gold | Returns the number of gold coins given to the mob. |
| $platinum | Returns the number of platinum coins given to the mob. |
| $x | The X coordinate of the NPC. |
| $y | The Y coordinate of the NPC. |
| $z | The Z coordinate of the NPC. |
| $h | The heading of the NPC. |



