# Entity List Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$entity_list->CanAddHateForMob(mob* target)
$entity_list->Clear()
$entity_list->ClearClientPetitionQueue()
$entity_list->ClearFeignAggro(mob* target)
$entity_list->DeleteNPCCorpses()
$entity_list->DeletePlayerCorpses()
$entity_list->DoubleAggro(*mob target)
$entity_list->Fighting(mob* target)
$entity_list->FindDoor(uint32 door_id)
$entity_list->GetClientByAccID(uint32 account_id)
$entity_list->GetClientByCharID(uint32 character_id)
$entity_list->GetClientByID(uint16 client_id)
$entity_list->GetClientByName(name)
$entity_list->GetClientByWID(uint32 wid)
$entity_list->GetClientList()
$entity_list->GetCorpseByID(id)
$entity_list->GetCorpseByName(name)
$entity_list->GetCorpseByOwner(client)
$entity_list->GetCorpseList()
$entity_list->GetDoorsByDBID(uint32 database_id)
$entity_list->GetDoorsByDoorID(uint32 door_id)
$entity_list->GetDoorsByID(uint32 entity_id)
$entity_list->GetDoorsList()
$entity_list->GetGroupByClient(client* client)
$entity_list->GetGroupByID(id)
$entity_list->GetGroupByLeaderName(leader)
$entity_list->GetGroupByMob(mob* mob)
$entity_list->GetMob(name)
$entity_list->GetMobByID(id)
$entity_list->GetMobByNpcTypeID(get_id)
$entity_list->GetMobID(id)
$entity_list->GetMobList()
$entity_list->GetNPCByID(id)
$entity_list->GetNPCByNPCTypeID(npc_id)
$entity_list->GetNPCBySpawnID(spawn_id)
$entity_list->GetNPCList()
$entity_list->GetObjectByDBID(uint32 database_id)
$entity_list->GetObjectByID(uint32 entity_id)
$entity_list->GetObjectList()
$entity_list->GetRaidByClient(client)
$entity_list->GetRaidByID(id)
$entity_list->GetRandomClient(float X, float Y, float Z, float distance, [client* exclude_client = nullptr])
$entity_list->HalveAggro(mob* target)
$entity_list->MakeNameUnique(string name)
$entity_list->Message(uint32 guild_id, uint32 emote_color_type, string message)
$entity_list->MessageClose(mob* sender, bool skip_sender, float distance, uint32 emote_color_type, string message)
$entity_list->MessageGroup(mob* sender, bool skip_close, uint32 emote_color_type, string message)
$entity_list->MessageStatus(uint32 guild_id, uint32 emote_color_type, string message)
$entity_list->OpenDoorsNear(npc* opener)
$entity_list->RemoveAllClients()
$entity_list->RemoveAllCorpses()
$entity_list->RemoveAllDoors()
$entity_list->RemoveAllGroups()
$entity_list->RemoveAllMobs()
$entity_list->RemoveAllNPCs()
$entity_list->RemoveAllObjects()
$entity_list->RemoveAllTraps()
$entity_list->RemoveClient(delete_id)
$entity_list->RemoveCorpse(delete_id)
$entity_list->RemoveDoor(delete_id)
$entity_list->RemoveEntity(uint16 id)
$entity_list->RemoveFromHateLists(mob* mob, [bool set_to_one = false])
$entity_list->RemoveFromTargets(mob* target)
$entity_list->RemoveGroup(delete_id)
$entity_list->RemoveMob(delete_id)
$entity_list->RemoveNPC(delete_id)
$entity_list->RemoveObject(delete_id)
$entity_list->RemoveTrap(delete_id)
$entity_list->ReplaceWithTarget(mob* old_mob, mob* new_target)
$entity_list->SignalAllClients(uint32 data)
$entity_list->SignalMobsByNPCID(uint32 npc_type_id, int signal_id)
$entity_list->ValidMobByNpcTypeID(get_id)
```
{% endtab %}

{% tab title="Lua" %}
```lua
entity_list:CanAddHateForMob(Lua_Mob p); -- bool
entity_list:ChannelMessage(Lua_Mob from, int channel_num, int language, const char *message); -- void
entity_list:ClearClientPetitionQueue(); -- void
entity_list:ClearFeignAggro(Lua_Mob who); -- void
entity_list:DeleteNPCCorpses(); -- int
entity_list:DeletePlayerCorpses(); -- int
entity_list:DoubleAggro(Lua_Mob who); -- void
entity_list:Fighting(Lua_Mob who); -- bool
entity_list:FilteredMessageClose(Lua_Mob sender, bool skip_sender, float dist, uint32 type, int filter, const char *message); -- void
entity_list:FindDoor(uint32 id); -- Lua_Door
entity_list:GetClientByAccID(uint32 acct_id); -- Lua_Client
entity_list:GetClientByCharID(uint32 char_id); -- Lua_Client
entity_list:GetClientByID(int id); -- Lua_Client
entity_list:GetClientByName(const char *name); -- Lua_Client
entity_list:GetClientByWID(uint32 wid); -- Lua_Client
entity_list:GetClientList(); -- Lua_Client_List
entity_list:GetCorpseByID(int id); -- Lua_Corpse
entity_list:GetCorpseByName(const char *name); -- Lua_Corpse
entity_list:GetCorpseByOwner(Lua_Client client); -- Lua_Corpse
entity_list:GetCorpseList(); -- Lua_Corpse_List
entity_list:GetDoorsByDBID(uint32 db_id); -- Lua_Door
entity_list:GetDoorsByDoorID(uint32 door_id); -- Lua_Door
entity_list:GetDoorsByID(int id); -- Lua_Door
entity_list:GetDoorsList(); -- Lua_Doors_List
entity_list:GetGroupByClient(Lua_Client client); -- Lua_Group
entity_list:GetGroupByID(int id); -- Lua_Group
entity_list:GetGroupByLeaderName(const char *name); -- Lua_Group
entity_list:GetGroupByMob(Lua_Mob mob); -- Lua_Group
entity_list:GetMob(const char *name); -- Lua_Mob
entity_list:GetMob(int id); -- Lua_Mob
entity_list:GetMobByNpcTypeID(int npc_type); -- Lua_Mob
entity_list:GetMobID(int id); -- Lua_Mob
entity_list:GetMobList(); -- Lua_Mob_List
entity_list:GetNPCByID(int id); -- Lua_NPC
entity_list:GetNPCByNPCTypeID(int npc_type); -- Lua_NPC
entity_list:GetNPCBySpawnID(int spawn_id); -- Lua_NPC
entity_list:GetNPCList(); -- Lua_NPC_List
entity_list:GetObjectByDBID(uint32 db_id); -- Lua_Object
entity_list:GetObjectByID(int id); -- Lua_Object
entity_list:GetObjectList(); -- Lua_Object_List
entity_list:GetRaidByClient(Lua_Client client); -- Lua_Raid
entity_list:GetRaidByID(int id); -- Lua_Raid
entity_list:GetRandomClient(float x, float y, float z, float dist); -- Lua_Client
entity_list:GetRandomClient(float x, float y, float z, float dist, Lua_Client exclude); -- Lua_Client
entity_list:GetShuffledClientList(); -- Lua_Client_List
entity_list:GetSpawnByID(uint32 id); -- Lua_Spawn
entity_list:GetSpawnList(); -- Lua_Spawn_List
entity_list:HalveAggro(Lua_Mob who); -- void
entity_list:IsMobSpawnedByNpcTypeID(int npc_type); -- bool
entity_list:MakeNameUnique(const char *name); -- std::string
entity_list:Message(uint32 guild_dbid, uint32 type, const char *message); -- void
entity_list:MessageClose(Lua_Mob sender, bool skip_sender, float dist, uint32 type, const char *message); -- void
entity_list:MessageGroup(Lua_Mob who, bool skip_close, uint32 type, const char *message); -- void
entity_list:MessageStatus(uint32 guild_dbid, int min_status, uint32 type, const char *message); -- void
entity_list:OpenDoorsNear(Lua_Mob opener); -- void
entity_list:RemoveFromHateLists(Lua_Mob who); -- void
entity_list:RemoveFromHateLists(Lua_Mob who, bool set_to_one); -- void
entity_list:RemoveFromTargets(Lua_Mob mob); -- void
entity_list:RemoveFromTargets(Lua_Mob mob, bool RemoveFromXTargets); -- void
entity_list:RemoveNumbers(const char *name); -- std::string
entity_list:ReplaceWithTarget(Lua_Mob target, Lua_Mob new_target); -- void
entity_list:SignalAllClients(int signal); -- void
entity_list:SignalMobsByNPCID(uint32 npc_id, int signal); -- void
```
{% endtab %}
{% endtabs %}

