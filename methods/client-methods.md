---
description: These are the Client object methods available through the EQEmu Quest API
---

# Client Methods

{% hint style="info" %}
We are actively working on a system to explore the EQEmu Quest API.  Please cross-reference with the new system as needed.

* Spire Quest API Explorer for [**Perl Client Methods**](http://spire.akkadius.com/quest-api-explorer?lang=perl&type=Client)
* Spire Quest API Explorer for [**Lua Client Methods**](http://spire.akkadius.com/quest-api-explorer?lang=lua&type=Client)\*\*\*\*
{% endhint %}

{% tabs %}
{% tab title="Perl" %}
```perl
$client->AccountID()
$client->AccountName()
$client->AddAAPoints(uint32 points)
$client->AddAlternateCurrencyValue(uint32 currency_id, int32 amount)
$client->AddCrystals(uint32 radiant_count, uint32 ebon_count)
$client->AddEXP(uint32 experience_points)
$client->AddLevelBasedExp(uint8 exp_percentage, uint8 max_level = 0, bool ignore_mods = false)
$client->AddMoneyToPP(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, bool update_client)
$client->AddPVPPoints(uint32 points)
$client->AddSkill(int skill_id, uint16 value)
$client->Admin()
$client->AssignTask(int task_id, int npc_id, [bool enforce_level_requirement = false])
$client->AssignToInstance(uint16 instance_id)
$client->AutoSplitEnabled()
$client->BreakInvis()
$client->CalcPriceMod(mob*, [bool reverse = false])
$client->CanHaveSkill(int skill_id)
$client->ChangeLastName(string last_name)
$client->CharacterID()
$client->CheckIncreaseSkill(int skill_id, int chance_modifier = 0)
$client->CheckSpecializeIncrease(uint16 spell_id)
$client->ClearCompassMark()
$client->ClearZoneFlag(uint32 zone_id)
$client->Connected()
$client->DecreaseByID(uint32 type, unit8 amount)
$client->DeleteItemInInventory(int16 slot_id, [int8 quantity = 0], [bool client_update = false])
$client->Disconnect()
$client->DropItem(int16 slot_id)
$client->Duck()
$client->DyeArmorBySlot(uint8 slot, uint8 red, uint8 green, uint8 blue, [uint8 use_tint = 0x00])
$client->Escape()
$client->ExpeditionMessage(int expedition_id, string message)
$client->FailTask(int task_id)
$client->FindMemmedSpellBySlot(int slot)
$client->ForageItem()
$client->GMKill()
$client->GetAAExp()
$client->GetAALevel(uint32 aa_skill_id)
$client->GetAAPercent()
$client->GetAAPoints()
$client->GetAccountFlag(string flag)
$client->GetAggroCount()
$client->GetAllMoney()
$client->GetAlternateCurrencyValue(uint32 currency_id)
$client->GetAnon()
$client->GetAugmentAt(uint32 slot, uint32 aug_slot)
$client->GetAugmentIDAt(int16 slot_id, int16 aug_slot)
$client->GetBaseAGI()
$client->GetBaseCHA()
$client->GetBaseDEX()
$client->GetBaseFace()
$client->GetBaseINT()
$client->GetBaseRace()
$client->GetBaseSTA()
$client->GetBaseSTR()
$client->GetBaseWIS()
$client->GetBecomeNPCLevel()
$client->GetBindHeading(int index = 0)
$client->GetBindX(int index = 0)
$client->GetBindY(int index = 0)
$client->GetBindZ(int index = 0)
$client->GetBindZoneID(int index = 0)
$client->GetCarriedMoney()
$client->GetCharacterFactionLevel(int32 faction_id)
$client->GetClientVersion()
$client->GetClientVersionBit()
$client->GetCorpseCount()
$client->GetCorpseID(uint8 corpse)
$client->GetCorpseItemAt(uint32 corpse_id, uint16 slot_id)
$client->GetCustomItemData(int16 slot_id, string identifier)
$client->GetDisciplineTimer(uint32 timer_id)
$client->GetDiscSlotBySpellID(int32 spell_id)
$client->GetDisplayAC()
$client->GetDuelTarget()
$client->GetEXP()
$client->GetEbonCrystals()
$client->GetEndurance()
$client->GetEnduranceRatio()
$client->GetFace()
$client->GetFactionLevel(uint32 character_id, uint32 npc_id, uint32 player_race_id, uint32 player_class_id, uint32 player_deity_id, uint32 player_faction_id, mob*)
$client->GetFeigned()
$client->GetFreeSpellBookSlot(uint32 start_slot = 0)
$client->GetGM()
$client->GetGroup()
$client->GetGroupPoints()
$client->GetHorseId()
$client->GetHunger()
$client->GetIP()
$client->GetInstanceID()
$client->GetInstrumentMod(uint16 spell_id)
$client->GetItemAt(uint32 slot)
$client->GetItemIDAt(int16 slot_id)
$client->GetItemInInventory(int16 slot_id)
$client->GetLDoNLosses()
$client->GetLDoNLossesTheme(int32 theme)
$client->GetLDoNPointsTheme(int32 theme)
$client->GetLDoNWins()
$client->GetLDoNWinsTheme(int32 theme)
$client->GetLanguageSkill(uint16 lanuage_id)
$client->GetLastName()
$client->GetMaxEndurance()
$client->GetModCharacterFactionLevel(int32 faction_id)
$client->GetPVP()
$client->GetPVPPoints()
$client->GetRadiantCrystals()
$client->GetRaid()
$client->GetRaidPoints()
$client->GetRawItemAC()
$client->GetRawSkill(int skill_id)
$client->GetSkill(uint16 skill_id)
$client->GetSkillPoints()
$client->GetSpellBookSlotBySpellID(uint32 spell_id)
$client->GetSpentAA()
$client->GetStartZone()
$client->GetTargetRingX()
$client->GetTargetRingY()
$client->GetTargetRingZ()
$client->GetTaskActivityDoneCount(int task_id, int activity_id)
$client->GetThirst()
$client->GetTotalSecondsPlayed()
$client->GetWeight()
$client->GoFish()
$client->GrantAlternateAdvancementAbility(int aa_id, int points, [bool ignore_cost = false])
$client->GuildID()
$client->GuildRank()
$client->HasSkill(int skill_id)
$client->HasSpellScribed(int spell_id)
$client->HasZoneFlag(uint32 zone_id)
$client->Hungry()
$client->InZone()
$client->IncStats(uint8 type, uint16 increase_val)
$client->IncreaseLanguageSkill(int skill_id, int value = 1)
$client->IncreaseSkill(int skill_id, int value = 1)
$client->IncrementAA(uint32 aa_skill_id)
$client->IsBecomeNPC()
$client->IsCrouching()
$client->IsDueling()
$client->IsGrouped()
$client->IsLD()
$client->IsMedding()
$client->IsRaidGrouped()
$client->IsSitting()
$client->IsStanding()
$client->IsTaskActive(int task_id)
$client->IsTaskActivityActive(int task_id, int activity_id)
$client->IsTaskCompleted(int task_id)
$client->KeyRingAdd(uint32 item_id)
$client->KeyRingCheck(uint32 item_id)
$client->Kick()
$client->LearnRecipe(uint32 recipe_id)
$client->LeaveGroup()
$client->LoadZoneFlags()
$client->MarkCompassLoc(float X, float Y, float Z)
$client->MaxSkill(uint16 skill_id, uint16 class_id, uint16 level)
$client->MemSpell(uint16 spell_id, int slot, [bool update_client = true])
$client->MemmedCount()
$client->MovePC(uint32 zone_id, float X, float Y, float Z, float heading)
$client->MovePCInstance(uint32 zone_id, uint32 instance_id, float X, float Y, float Z, float heading)
$client->MoveZone(const char *zone_short_name)
$client->MoveZoneGroup(const char *zone_short_name)
$client->MoveZoneRaid(const char *zone_short_name)
$client->MoveZoneInstance(uint16 instance_id)
$client->MoveZoneInstanceGroup(uint16 instance_id)
$client->MoveZoneInstanceRaid(uint16 instance_id)
$client->NotifyNewTitlesAvailable()
$client->NPCSpawn(npc*, string option, uint32 respawn_time=1200)
$client->NukeItem(uint32 item_id, [uint8 slot_to_check])
$client->OpenLFGuildWindow()
$client->PlayMP3(string file_name)
$client->Popup2(string title, string text, uint32 popup_id, uint32 negative_id, uint32 buttons, uint32 duration, string button_name_0, string button_name_1, uint32 sound_controls)
$client->QuestReward(int32 mob, int32 copper, int32 silver, int32 gold, int32 platinum, int32 item_id, int32 exp, [bool faction = false])
$client->ReadBook(char* book_test, uint8 type)
$client->RefundAA()
$client->RemoveFromInstance(uint16 instance_id)
$client->RemoveNoRent()
$client->ResetAA()
$client->ResetDisciplineTimer(uint32 timer_id)
$client->ResetTrade()
$client->Save(uint8 commit_now)
$client->SaveBackup()
$client->ScribeSpell(uint16 spell_id, int slot, [bool update_client = true])
$client->SendColoredText(uint32 color, string message)
$client->SendMarqueeMessage(uint32 type, uint32 priority, uint32 fade_in, uint32 fade_out, uint32 duration, string msg)
$client->SendOPTranslocateConfirm(mob* caster, int32 spell_id)
$client->SendSound()
$client->SendTargetCommand(int32 entity_id)
$client->SendToGuildHall()
$client->SendToInstance(sting type, string short name, uint32 instance version, float x, float y, float z, float heading, string instance identifier, uint32 duration)
$client->SendWebLink(string website_url)
$client->SendZoneFlagInfo(client* to)
$client->SetAAPoints(uint32 points)
$client->SetAATitle(string text, [bool save = false])
$client->SetAccountFlag(string flag, string value)
$client->SetAlternateCurrencyValue(uint32 currency_id, int32 amount)
$client->SetBaseClass(uint32 class_id)
$client->SetBaseGender(uint32 gender_id)
$client->SetBaseRace(uint32 race_id)
$client->SetBecomeNPC(flag)
$client->SetBecomeNPCLevel(level)
$client->SetBindPoint(int to_zone = -1, int to_instance = 0, float new_x = 0.0f, float new_y = 0.0f, float new_z = 0.0f)
$client->SetCustomItemData(int16 slot_id, string identifier, string value)
$client->SetDeity(uint32 deity_id)
$client->SetDuelTarget(set_id)
$client->SetDueling(duel)
$client->SetEXP(uint32 experience_points, uint32 aa_experience_points, [bool resexp=false])
$client->SetEndurance(endurance)
$client->SetFactionLevel(uint32 character_id, uint32 npc_id, uint8 character_class, uint8 character_race, uint8 character_deity)
$client->SetFactionLevel2(uint32 character_id, int32 faction_id, uint8 character_class, uint8 character_race, uint8 character_deity, int32 value, uint8 temp)
$client->SetFeigned(in_feigned)
$client->SetGM(bool toggle)
$client->SetHorseId(horseid_in)
$client->SetHunger(in_hunger)
$client->SetHunger(int32 hunger_amount, int32 thirst_amount)
$client->SetLanguageSkill(int language_id, int value)
$client->SetMaterial(int16 slot_id, uint32 item_id)
$client->SetPVP(bool toggle)
$client->SetPrimaryWeaponOrnamentation(model_id)
$client->SetSecondaryWeaponOrnamentation(model_id)
$client->SetSkill(int skill_id, uint16 value)
$client->SetSkillPoints(inp)
$client->SetStats(uint8 type, uint16 increase_val)
$client->SetThirst(int32 in_thirst)
$client->SetTint(int16 slot_id, uint32 color)
$client->SetTitleSuffix(string text, [bool save = false])
$client->SetZoneFlag(uint32 zone_id)
$client->SignalClient(uint32 data)
$client->SilentMessage(string message)
$client->SlotConvert2(uint8 slot)
$client->Stand()
$client->SummonItem(uint32 item_id, [int16 charges = -1], [bool attune = false], [uint32 aug1 = 0], [uint32 aug2 = 0], [uint32 aug3 = 0], [uint32 aug4 = 0], [uint32 aug5 = 0], [uint16 slot_id = cursor])
$client->TGB()
$client->TakeMoneyFromPP(uint32 copper, bool update_client = false)
$client->Thirsty()
$client->TrainDiscBySpellID(int32 spell_id)
$client->Undye()
$client->UnmemSpell(int slot, [bool update_client = true])
$client->UnmemSpellAll([bool update_client = true])
$client->UnmemSpellBySpellID(int32 spell_id)
$client->UnscribeSpell(int slot, [bool update_client = true])
$client->UnscribeSpellAll([bool update_client = true])
$client->UntrainDisc(int slot, [bool update_client = true])
$client->UntrainDiscAll([update_client = true])
$client->UpdateAdmin(bool from_db = true)
$client->UpdateGroupAAs(int32 points, uint32 type)
$client->UpdateLDoNPoints(int32 points, uint32 theme)
$client->UpdateTaskActivity(int task_id, int activity_id, int count, [bool ignore_quest_update = false])
$client->UpdateWho(uint8 remove = 0)
$client->UseDiscipline(int32 spell_id, int32 target)
$client->WorldKick()
```
{% endtab %}

{% tab title="Lua" %}
```lua
client:AccountID(); -- uint32
client:AddAAPoints(int points); -- void
client:AddAlternateCurrencyValue(uint32 currency, int amount); -- void
client:AddCrystals(uint32 radiant, uint32 ebon); -- void
client:AddEXP(uint32 add_exp); -- void
client:AddEXP(uint32 add_exp, int conlevel); -- void
client:AddEXP(uint32 add_exp, int conlevel, bool resexp); -- void
client:AddLevelBasedExp(int exp_pct); -- void
client:AddLevelBasedExp(int exp_pct, int max_level); -- void
client:AddLevelBasedExp(int exp_pct, int max_level, bool ignore_mods); -- void
client:AddMoneyToPP(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, bool update_client); -- void
client:AddPVPPoints(uint32 points); -- void
client:AddSkill(int skill_id, int value); -- void
client:Admin(); -- int
client:AssignTask(int task, int npc_id); -- void
client:AssignTask(int task, int npc_id, bool enforce_level_requirement); -- void
client:AssignToInstance(int instance_id); -- void
client:AutoSplitEnabled(); -- bool
client:BreakInvis(); -- void
client:CalcATK(); -- int
client:CalcCurrentWeight(); -- int
client:CalcPriceMod(Lua_Mob other, bool reverse); -- float
client:CanHaveSkill(int skill_id); -- bool
client:ChangeLastName(const char *in); -- void
client:CharacterID(); -- uint32
client:CheckIncreaseSkill(int skill_id, Lua_Mob target); -- void
client:CheckIncreaseSkill(int skill_id, Lua_Mob target, int chance_mod); -- void
client:CheckSpecializeIncrease(int spell_id); -- void
client:ClearCompassMark(); -- void
client:ClearZoneFlag(int zone_id); -- void
client:Connected(); -- bool
client:DecreaseByID(uint32 type, int amt); -- bool
client:DeleteItemInInventory(int slot_id, int quantity); -- void
client:DeleteItemInInventory(int slot_id, int quantity, bool update_client); -- void
client:DisableAreaEndRegen(); -- void
client:DisableAreaHPRegen(); -- void
client:DisableAreaManaRegen(); -- void
client:DisableAreaRegens(); -- void
client:Disconnect(); -- void
client:DropItem(int slot_id); -- void
client:Duck(); -- void
client:DyeArmorBySlot(uint8 slot, uint8 red, uint8 green, uint8 blue); -- void
client:DyeArmorBySlot(uint8 slot, uint8 red, uint8 green, uint8 blue, uint8 use_tint); -- void
client:EnableAreaEndRegen(int value); -- void
client:EnableAreaHPRegen(int value); -- void
client:EnableAreaManaRegen(int value); -- void
client:EnableAreaRegens(int value); -- void
client:Escape(); -- void
client:FailTask(int task); -- void
client:FilteredMessage(Mob *sender, uint32 type, int filter, const char *message); -- void
client:FindMemmedSpellBySlot(int slot); -- uint16
client:FindSpellBookSlotBySpellID(int spell_id); -- int
client:ForageItem(); -- void
client:ForageItem(bool guarantee); -- void
client:Freeze(); -- void
client:GetAAExp(); -- uint32
client:GetAAPercent(); -- uint32
client:GetAAPoints(); -- int
client:GetAccountAge(); -- int
client:GetAccountFlag(std::string flag); -- std::string
client:GetAggroCount(); -- int
client:GetAllMoney(); -- uint64
client:GetAlternateCurrencyValue(uint32 currency); -- int
client:GetAnon(); -- bool
client:GetAugmentIDAt(int slot_id, int aug_slot); -- int
client:GetBaseAGI(); -- int
client:GetBaseCHA(); -- int
client:GetBaseDEX(); -- int
client:GetBaseFace(); -- int
client:GetBaseINT(); -- int
client:GetBaseRace(); -- int
client:GetBaseSTA(); -- int
client:GetBaseSTR(); -- int
client:GetBaseWIS(); -- int
client:GetBindHeading(); -- float
client:GetBindHeading(int index); -- float
client:GetBindX(); -- float
client:GetBindX(int index); -- float
client:GetBindY(); -- float
client:GetBindY(int index); -- float
client:GetBindZ(); -- float
client:GetBindZ(int index); -- float
client:GetBindZoneID(); -- uint32
client:GetBindZoneID(int index); -- uint32
client:GetCarriedMoney(); -- uint64
client:GetCharacterFactionLevel(int faction_id); -- int
client:GetClientVersion(); -- int
client:GetClientVersionBit(); -- uint32
client:GetCorpseCount(); -- int
client:GetCorpseID(int corpse); -- int
client:GetCorpseItemAt(int corpse, int slot); -- int
client:GetDisciplineTimer(uint32 timer_id); -- uint32
client:GetDiscSlotBySpellID(int32 spell_id); -- int
client:GetDisplayAC()
client:GetDuelTarget(); -- int
client:GetEXP(); -- uint32
client:GetEbonCrystals(); -- uint32
client:GetEndurance(); -- int
client:GetEndurancePercent(); -- int
client:GetFace(); -- int
client:GetFactionLevel(uint32 char_id, uint32 npc_id, uint32 race, uint32 class_, uint32 deity, uint32 faction, Lua_NPC npc); -- int
client:GetFeigned(); -- bool
client:GetGM(); -- bool
client:GetGroup(); -- Lua_Group
client:GetGroupPoints(); -- uint32
client:GetHorseId(); -- int
client:GetHunger(); -- int
client:GetIP(); -- uint32
client:GetInstrumentMod(int spell_id); -- int
client:GetInventory(); -- Lua_Inventory
client:GetItemIDAt(int slot_id); -- int
client:GetLDoNLosses(); -- int
client:GetLDoNLossesTheme(int theme); -- int
client:GetLDoNPointsTheme(int theme); -- int
client:GetLDoNWins(); -- int
client:GetLDoNWinsTheme(int theme); -- int
client:GetLanguageSkill(int skill_id); -- int
client:GetMaxEndurance(); -- int
client:GetModCharacterFactionLevel(int faction); -- int
client:GetMoney(uint8 type, uint8 subtype); -- uint32
client:GetNextAvailableSpellBookSlot(); -- int
client:GetNextAvailableSpellBookSlot(int start); -- int
client:GetPVP(); -- bool
client:GetPVPPoints(); -- uint32
client:GetRadiantCrystals(); -- uint32
client:GetRaid(); -- Lua_Raid
client:GetRaidPoints(); -- uint32
client:GetRawItemAC(); -- int
client:GetRawSkill(int skill_id); -- int
client:GetSkillPoints(); -- int
client:GetSpentAA(); -- int
client:GetStartZone(); -- int
client:GetThirst(); -- int
client:GetTotalSecondsPlayed(); -- uint32
client:GetWeight(); -- int
client:GoFish(); -- void
client:GrantAlternateAdvancementAbility(int aa_id, int points); -- bool
client:GrantAlternateAdvancementAbility(int aa_id, int points, bool ignore_cost); -- bool
client:GuildID(); -- uint32
client:GuildRank(); -- int
client:HasSkill(int skill_id); -- bool
client:HasSpellScribed(int spell_id); -- bool
client:HasZoneFlag(int zone_id); -- bool
client:Hungry(); -- bool
client:InZone(); -- bool
client:IncStats(int type, int value); -- void
client:IncreaseLanguageSkill(int skill_id); -- void
client:IncreaseLanguageSkill(int skill_id, int value); -- void
client:IncreaseSkill(int skill_id); -- void
client:IncreaseSkill(int skill_id, int value); -- void
client:IncrementAA(int aa); -- void
client:IsCrouching(); -- bool
client:IsDead(); -- bool
client:IsDueling(); -- bool
client:IsGrouped(); -- bool
client:IsLD(); -- bool
client:IsMedding(); -- bool
client:IsRaidGrouped(); -- bool
client:IsSitting(); -- bool
client:IsStanding(); -- bool
client:IsTaskActive(int task); -- bool
client:IsTaskActivityActive(int task, int activity); -- bool
client:IsTaskCompleted(int task); -- bool
client:KeyRingAdd(uint32 item); -- void
client:KeyRingCheck(uint32 item); -- bool
client:Kick(); -- void
client:LearnRecipe(uint32 recipe); -- void
client:LeaveGroup(); -- void
client:MarkSingleCompassLoc(float in_x, float in_y, float in_z); -- void
client:MarkSingleCompassLoc(float in_x, float in_y, float in_z, int count); -- void
client:MaxSkill(int skill_id); -- int
client:MemSpell(int spell_id, int slot); -- void
client:MemSpell(int spell_id, int slot, bool update_client); -- void
client:MemmedCount(); -- int
client:MovePC(int zone, float x, float y, float z, float heading); -- void
client:MovePCInstance(int zone, int instance, float x, float y, float z, float heading); -- void
client:MoveZone(const char *zone_short_name); -- void
client:MoveZoneGroup(const char *zone_short_name); -- void
client:MoveZoneRaid(const char *zone_short_name); -- void
client:MoveZoneInstance(uint16 instance_id); -- void
client:MoveZoneInstanceGroup(uint16 instance_id); -- void
client:MoveZoneInstanceRaid(uint16 instance_id); -- void
client:NukeItem(uint32 item_num); -- void
client:NukeItem(uint32 item_num, int where_to_check); -- void
client:OpenLFGuildWindow(); -- void
client:PlayMP3(std::string file); -- void
client:PushItemOnCursor(Lua_ItemInst inst); -- bool
client:PutItemInInventory(int slot_id, Lua_ItemInst inst); -- bool
client:QuestReadBook(const char *text, int type); -- void
client:QuestReward(Lua_Mob target); -- void
client:QuestReward(Lua_Mob target, uint32 copper); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum, uint32 itemid); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum, uint32 itemid, uint32 exp); -- void
client:QuestReward(Lua_Mob target, uint32 copper, uint32 silver, uint32 gold, uint32 platinum, uint32 itemid, uint32 exp, bool faction); -- void
client:QueuePacket(Lua_Packet app); -- void
client:QueuePacket(Lua_Packet app, bool ack_req); -- void
client:QueuePacket(Lua_Packet app, bool ack_req, int client_connection_status); -- void
client:QueuePacket(Lua_Packet app, bool ack_req, int client_connection_status, int filter); -- void
client:RefundAA(); -- void
client:ResetAA(); -- void
client:ResetDisciplineTimer(uint32 timer_id); -- void
client:ResetTrade(); -- void
client:Save(); -- void
client:Save(int commit_now); -- void
client:SaveBackup(); -- void
client:ScribeSpell(int spell_id, int slot); -- void
client:ScribeSpell(int spell_id, int slot, bool update_client); -- void
client:SendColoredText(uint32 type, std::string msg); -- void
client:SendItemScale(Lua_ItemInst inst); -- void
client:SendMarqueeMessage(uint32 type, uint32 priority, uint32 fade_in, uint32 fade_out, uint32 duration, std::string msg); -- void
client:SendOPTranslocateConfirm(Lua_Mob caster, int spell_id); -- void
client:SendSound(); -- void
client:SendWebLink(const char *site); -- void
client:SendZoneFlagInfo(Lua_Client to); -- void
client:SetAAPoints(int points); -- void
client:SetAATitle(const char *title); -- void
client:SetAccountFlag(std::string flag, std::string val); -- void
client:SetAlternateCurrencyValue(uint32 currency, int amount); -- void
client:SetBaseClass(int v); -- void
client:SetBaseGender(int v); -- void
client:SetBaseRace(int v); -- void
client:SetBindPoint(); -- void
client:SetBindPoint(int to_zone); -- void
client:SetBindPoint(int to_zone, int to_instance); -- void
client:SetBindPoint(int to_zone, int to_instance, float new_x); -- void
client:SetBindPoint(int to_zone, int to_instance, float new_x, float new_y); -- void
client:SetBindPoint(int to_zone, int to_instance, float new_x, float new_y, float new_z); -- void
client:SetConsumption(int in_hunger, int in_thirst); -- void
client:SetDeity(int v); -- void
client:SetDuelTarget(int c); -- void
client:SetDueling(bool v); -- void
client:SetEXP(uint32 set_exp, uint32 set_aaxp); -- void
client:SetEXP(uint32 set_exp, uint32 set_aaxp, bool resexp); -- void
client:SetEndurance(int endur); -- void
client:SetFactionLevel(uint32 char_id, uint32 npc_id, int char_class, int char_race, int char_deity); -- void
client:SetFactionLevel2(uint32 char_id, int faction_id, int char_class, int char_race, int char_deity, int value, int temp); -- void
client:SetFeigned(bool v); -- void
client:SetGM(bool v); -- void
client:SetHorseId(int id); -- void
client:SetHunger(int in_hunger); -- void
client:SetLanguageSkill(int language, int value); -- void
client:SetMaterial(int slot_id, uint32 item_id); -- void
client:SetPVP(bool v); -- void
client:SetPrimaryWeaponOrnamentation(uint32 model_id); -- void
client:SetSecondaryWeaponOrnamentation(uint32 model_id); -- void
client:SetSkill(int skill_id, int value); -- void
client:SetSkillPoints(int skill); -- void
client:SetStartZone(int zone_id); -- void
client:SetStartZone(int zone_id, float x); -- void
client:SetStartZone(int zone_id, float x, float y); -- void
client:SetStartZone(int zone_id, float x, float y, float z); -- void
client:SetStats(int type, int value); -- void
client:SetThirst(int in_thirst); -- void
client:SetTint(int slot_id, uint32 color); -- void
client:SetTitleSuffix(const char *text); -- void
client:SetZoneFlag(int zone_id); -- void
client:Signal(uint32 id); -- void
client:Stand(); -- void
client:SummonItem(uint32 item_id); -- void
client:SummonItem(uint32 item_id, int charges); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5, bool attuned); -- void
client:SummonItem(uint32 item_id, int charges, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5, bool attuned, int to_slot); -- void
client:TGB(); -- bool
client:TakeMoneyFromPP(uint64 copper); -- bool
client:TakeMoneyFromPP(uint64 copper, bool update_client); -- bool
client:Thirsty(); -- bool
client:TrainDisc(int itemid); -- void
client:TrainDiscBySpellID(int32 spell_id); -- void
client:UnFreeze(); -- void
client:Undye(); -- void
client:UnmemSpell(int slot); -- void
client:UnmemSpell(int slot, bool update_client); -- void
client:UnmemSpellAll(); -- void
client:UnmemSpellAll(bool update_client); -- void
client:UnmemSpellBySpellID(int32 spell_id); -- void
client:UnscribeSpell(int slot); -- void
client:UnscribeSpell(int slot, bool update_client); -- void
client:UnscribeSpellAll(); -- void
client:UnscribeSpellAll(bool update_client); -- void
client:UntrainDisc(int slot); -- void
client:UntrainDisc(int slot, bool update_client); -- void
client:UntrainDiscAll(); -- void
client:UntrainDiscAll(bool update_client); -- void
client:UpdateGroupAAs(int points, uint32 type); -- void
client:UpdateLDoNPoints(int points, uint32 theme); -- void
client:UpdateTaskActivity(int task, int activity, int count); -- void
client:UseDiscipline(int spell_id, int target_id); -- bool
client:WorldKick(); -- void
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
$obj-&gt;$a is an example to access variable $a from object $obj
{% endhint %}

## Client Methods Explained

### AccountID

      **Parameter:**

      None.

      **Usage:**

      Returns the account ID of the client.

      **Example**

```perl
sub EVENT_SAY {
    if ($text=~/hail/i) {
        #:: Create a scalar variable to store the account ID of the client that triggered the event
        my $AccountID = $client->AccountID();
        #:: Send a message to the client in yellow (15) text
        $client->Message(15, "Your account ID is $AccountID.");
    }
}
```

### AccountName

      **Parameter:**

      None.

      **Usage:**

      Returns the account name of the client.

      **Example**

```perl
sub EVENT_SAY {
    if ($text=~/hail/i) {
        #:: Create a scalar variable to store the account name of the client that triggered the event
        my $AccountName = $client->AccountName();
        #:: Send a message to the client in yellow (15) text
        $client->Message(15, "Your account name is $AccountName.");
    }
}
```

### AddAAPoints

      **Parameter:**

     points _\(uint32\)_

      **Usage:**

      Add the specified number of AA points to the client.

      **Example**

```perl
sub EVENT_ITEM_CLICK {
    #:: Match item 123456 - Some Item
    if ($item == 123456) {
        #:: Award 20 AA points to the client who triggered the event
        $client->AddAAPoints(20);
    }
}
```

### AddAlternateCurrencyValue

      **Parameter:**

      currency\_id _\(uint32\)_ amount _\(int32\)_

      **Usage:**

      Add the specified amount of the specified currency to the client.

      **Example**

```perl
sub EVENT_ITEM_CLICK {
    #:: Match item 57810 - Bag of Doubloons
    if ($itemid == 57810) {
        #:: Give 79910 - Doubloon x100 to the client who triggered the event
        $client->AddAlternateCurrencyValue(79910, 100);
    }
}
```

### AddCrystals

      **Parameter:**

      radiant\_count _\(uint32\)_, ebon\_count _\(uint32\)_

      **Usage:**

      Add the specified amount of the Radiant or Ebon crystals to the client.

      **Example**

```perl
sub EVENT_ITEM_CLICK {
    #:: Match item 57816 - Bag of Ebon Crystals
    if ($itemid == 57816) {
        #:: Give 40902 - Ebon Crystal x100 to the client who triggered the event
        $client->AddCrystals(0, 100);
    }
}
```

### AddEXP

      **Parameter:**

      experience\_points _\(uint32\)_

      **Usage:**

      Add the specified amount of experience to the client.

      **Example**

```perl
sub EVENT_ITEM {
    #:: Match item 123456 - Some Item
    if (plugin::takeItem(123456 => 1) {
        #:: Grant 100 experience to the client who triggered the event
        $client->AddEXP(100);
    }
}
```

### AddLevelBasedExp

      **Parameter:**

      exp\_percentage _\(uint8\)_, max\_level _\(uint8\) \[default = 0\],_ ignore\_mods _\(bool\) \[default = false\]_

      **Usage:**

      Adds the specified percentage of experience at each level, up until the maximum level specified, to the client.  If the player's level exceeds the maximum level specified, the player would only be rewarded the percentage of the experience at the specified level.

      **Example**

```perl
sub EVENT_ITEM {
    #:: Match item 123456 - Some Item
    if (plugin::takeItem(123456 => 1) {
        #:: Grant 4 percent experience to the client who triggered the event up until level 15
        $client->AddLevelBasedExp(4, 15);
    }
}
```

### AddMoneyToPP

      **Parameter:**

      copper _\(uint32\)_, silver _\(uint32\)_, gold _\(uint32\)_, platinum _\(uint32\)_, update\_client _\(bool\)_

      **Usage:**

      Adds the amount of currency specified to the client.

      **Example**

```perl
sub EVENT_ITEM {
    #:: Match item 123456 - Some Item
    if (plugin::takeItem(123456 => 1) {
        #:: Give 1cp, 2sp, 3gp, 4pp to the client who triggered the event, but don't tell them about it
        $client->AddMoneyToPP(1, 2, 3, 4, 0);
    }
}
```

### AddPVPPoints

      **Parameter:**

      points _\(uint32\)_

      **Usage:**

      Adds the specified number of PVP points to the client.

      **Example**

```perl
sub EVENT_ITEM {
    #:: Match item 123456 - Some Item
    if (plugin::takeItem(123456 => 1) {
        #:: Grant one pvp point to the client who triggered the event
        $client->AddPVPPoints(1);
    }
}
```

### AddSkill

      **Parameter:**

      skill\_id _\(int\)_, value _\(uint16\)_

      **Usage:**

      Adds the specified skill level value to the specified skill for the client.

{% hint style="warning" %}
Note the difference between $client-&gt;AddSkill and $client-&gt;SetSkill
{% endhint %}

      **Example**

```perl
sub EVENT_COMBINE_SUCCESS {
    #:: Match Recipe 2686 - Hand Made Backpack by ID
    if ($recipe_id == 2686) {
        #:: Send the client a message in color 15 (yellow)
        $client->Message(15,"Wow, you did it--you won tailoring!");
        #:: Add 300 points to the Tailoring skill for the client that triggered the event
        $client->AddSkill(61, 300);
    }
}
```

### Admin

      **Parameter:**

      None.

      **Usage:**

      Returns the Admin account status of the client.

{% hint style="info" %}
Note that `$status` is exported by many events, should it prove more useful.
{% endhint %}

      **Example**

```perl
sub EVENT_SAY {
    if ($text=~/hail/i) {
        #:: Create a scalar variable to store admin status
        $GMstatus = $client->Admin();
        #:: Match if the account status is greater than one
        if ($GMstatus > 1) {
            quest::say("How ya doin', boss?");
        }
        else {
            quest::say("Hello, $name");
        }
    }
}
```

### AssignTask

      **Parameter:**

      task\_id _\(int\)_, npc\_id _\(int\)_, enforce\_level\_requirement _\(bool\) \[Default = false\]_

      **Usage:**

      Assigns the specified task, credited to the specified NPC, to the client.  Enforcing the level requirement of the task is optional, and defaults to false.

      **Example**

```perl
#:: Assign Task 105, credit the npc by id, with level requirement enforced
$client->AssignTask(105, $npc->GetID(), 1);
#:: Assign Task 104, credit the npc by id, ignore level requirement
$client->AssignTask(104, $npc->GetID());
```

### AssignToInstance

      **Parameter:**

      instance\_id _\(uint16\)_

      **Usage:**

      Assigns the specified instance to the client.

      **Example**

```perl
#:: Create a scalar variable to store the instance id
$InstanceID = quest::CreateInstance("soldungb", 0, 86400); #:: Instance of Sol B, based on version 0, for 86400 seconds (1 day)
#:: Assign the client to the instance
$client->AssignToInstance($InstanceID);
```

### AutoSplitEnabled

      **Parameter:**

      None.

      **Usage:**

      Turns on auto-split \(coin\) for the client.

      **Example**

```perl
sub EVENT_GROUP_CHANGE {
    #:: Turn on auto-split
    $client->AutoSplitEnabled()
}
```

### BreakInvis

      **Parameter:**

      None.

      **Usage:**

      Turns off invisibility effects for the client.

      **Example**

```perl
sub EVENT_CLICKDOOR {
    #:: Turn off invis for any client that clicks the door
    $client->BreakInvis()
}
```



