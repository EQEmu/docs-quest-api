# NPC Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$npc->AI_SetRoambox(float distance, float max_x, float min_x, float max_y, float min_y, [uint32 max_delay = 2500], [uint32 min_delay = 2500])
$npc->AddAISpell(int priority, int spell_id, int type, int mana_cost, int recast_delay, int resist_adjust)
$npc->AddCash(uint16 copper, uint16 silver, uint16 gold, uint16 platinum)
$npc->AddDefensiveProc(int spell_id, int chance)
$npc->AddItem(uint32 item_id, [uint16 charges = 0], [bool equip_item = true], [uint32 aug1 = 0], [uint32 aug2 = 0], [uint32 aug3 = 0], [uint32 aug4 = 0], [uint32 aug5 = 0], [uint32 aug6 = 0])
$npc->AddLootTable([uint32 loottable_id])
$npc->AddMeleeProc(int spell_id, int chance)
$npc->AddRangedProc(int spell_id, int chance)
$npc->AssignWaypoints(uint32 grid_id)
$npc->CalculateNewWaypoint()
$npc->ChangeLastName(string name)
$npc->CheckNPCFactionAlly(int32 faction_id)
$npc->ClearItemList()
$npc->ClearLastName()
$npc->CountLoot()
$npc->DisplayWaypointInfo(client* target)
$npc->DoClassAttacks(mob* target)
$npc->GetAccuracyRating()
$npc->GetAttackDelay()
$npc->GetAttackSpeed()
$npc->GetAvoidanceyRating()
$npc->GetCombatState()
$npc->GetCopper()
$npc->GetGold()
$npc->GetGrid()
$npc->GetGuardPointX()
$npc->GetGuardPointY()
$npc->GetGuardPointZ()
$npc->GetLoottableID()
$npc->GetMaxDMG()
$npc->GetMaxDamage(uint8 target_level)
$npc->GetMaxWp()
$npc->GetMinDMG()
$npc->GetNPCFactionID()
$npc->GetNPCHate(mob* entity)
$npc->GetNPCSpellsID()
$npc->GetPetSpellID()
$npc->GetPlatinum()
$npc->GetPrimSkill()
$npc->GetPrimaryFaction()
$npc->GetScore()
$npc->GetSecSkill()
$npc->GetSilver()
$npc->GetSlowMitigation()
$npc->GetSp2()
$npc->GetSpawnKillCount()
$npc->GetSpawnPointH()
$npc->GetSpawnPointID()
$npc->GetSpawnPointX()
$npc->GetSpawnPointY()
$npc->GetSpawnPointZ()
$npc->GetSpellFocusDMG()
$npc->GetSpellFocusHeal()
$npc->GetSwarmOwner()
$npc->GetSwarmTarget()
$npc->GetWaypointMax()
$npc->IsAnimal()
$npc->IsGuarding()
$npc->IsOnHatelist(mob* target)
$npc->MerchantCloseShop()
$npc->MerchantOpenShop()
$npc->ModifyNPCStat(string key, string value)
$npc->MoveTo(float X, float Y, float Z, [float heading], [bool save_guard_location = false])
$npc->NextGuardPosition()
$npc->PauseWandering(int pause_time)
$npc->PickPocket(client* thief)
$npc->RecalculateSkills()
$npc->RemoveAISpell(int spell_id)
$npc->RemoveCash()
$npc->RemoveDefensiveProc(int spell_id)
$npc->RemoveFromHateList(mob* target)
$npc->RemoveItem(uint32 item_id, [uint16 quantity = 0], [uint16 slot_id = 0])
$npc->RemoveMeleeProc(int spell_id)
$npc->RemoveRangedProc(int spell_id)
$npc->ResumeWandering()
$npc->SaveGuardSpot(X, Y, Z, heading)
$npc->SetCopper(uint32 copper_amount)
$npc->SetGold(uint32 gold_amount)
$npc->SetGrid(int32 grid_id)
$npc->SetNPCFactionID(int32 faction_id)
$npc->SetPetSpellID(uint16 amount)
$npc->SetPlatinum(uint32 platinum_amount)
$npc->SetPrimSkill(int skill_id)
$npc->SetSaveWaypoint(uint16 waypoint)
$npc->SetSecSkill(int skill_id)
$npc->SetSilver(uint32 silver_amount)
$npc->SetSimpleRoamBox(box_size, move_distance, move_delay)
$npc->SetSp2(uint32 set_spawn_group_id)
$npc->SetSpellFocusDMG(int new_spell_focus_dmg)
$npc->SetSpellFocusHeal(int32 new_spell_focus_heal)
$npc->SetSwarmTarget(int target_id)
$npc->SetTaunting(bool toggle)
$npc->SetWaypointPause()
$npc->SignalNPC(int signal_id)
$npc->StartSwarmTimer(uint32 duration)
$npc->StopWandering()
$npc->UpdateWaypoint(int wp_index)
```
{% endtab %}

{% tab title="Lua" %}
```lua
npc:AI_SetRoambox(float dist, float max_x, float min_x, float max_y, float min_y); -- void
npc:AI_SetRoambox(float dist, float max_x, float min_x, float max_y, float min_y, uint32 delay, uint32 mindelay); -- void
npc:AddAISpell(int priority, int spell_id, int type, int mana_cost, int recast_delay, int resist_adjust); -- void
npc:AddAISpell(int priority, int spell_id, int type, int mana_cost, int recast_delay, int resist_adjust, int min_hp, int max_hp); -- void
npc:AddCash(int copper, int silver, int gold, int platinum); -- void
npc:AddItem(int item_id, int charges); -- void
npc:AddItem(int item_id, int charges, bool equip); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3, int aug4); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3, int aug4, int aug5); -- void
npc:AddItem(int item_id, int charges, bool equip, int aug1, int aug2, int aug3, int aug4, int aug5, int aug6); -- void
npc:AddLootTable(); -- void
npc:AddLootTable(int id); -- void
npc:AssignWaypoints(int grid); -- void
npc:CalculateNewWaypoint(); -- void
npc:CheckNPCFactionAlly(int faction); -- int
npc:ClearItemList(); -- void
npc:CountLoot(); -- int
npc:DisplayWaypointInfo(Lua_Client to); -- void
npc:DoClassAttacks(Lua_Mob target); -- void
npc:GetAccuracyRating(); -- int
npc:GetAttackDelay(); -- int
npc:GetAttackSpeed(); -- float
npc:GetAvoidanceRating(); -- int
npc:GetCopper(); -- uint32
npc:GetFollowCanRun(); -- bool
npc:GetFollowDistance(); -- int
npc:GetFollowID(); -- int
npc:GetGold(); -- uint32
npc:GetGrid(); -- int
npc:GetGuardPointX(); -- float
npc:GetGuardPointY(); -- float
npc:GetGuardPointZ(); -- float
npc:GetLoottableID(); -- int
npc:GetMaxDMG(); -- uint32
npc:GetMaxDamage(int level); -- uint32
npc:GetMaxWp(); -- int
npc:GetMinDMG(); -- uint32
npc:GetNPCFactionID(); -- int
npc:GetNPCHate(Lua_Mob ent); -- int
npc:GetNPCSpellsID(); -- int
npc:GetPetSpellID(); -- int
npc:GetPlatinum(); -- uint32
npc:GetPrimSkill(); -- int
npc:GetPrimaryFaction(); -- int
npc:GetRawAC(); -- int
npc:GetScore(); -- int
npc:GetSecSkill(); -- int
npc:GetSilver(); -- uint32
npc:GetSlowMitigation(); -- float
npc:GetSp2(); -- uint32
npc:GetSpawnKillCount(); -- int
npc:GetSpawnPointH(); -- float
npc:GetSpawnPointID(); -- int
npc:GetSpawnPointX(); -- float
npc:GetSpawnPointY(); -- float
npc:GetSpawnPointZ(); -- float
npc:GetSpellFocusDMG(); -- int
npc:GetSpellFocusHeal(); -- int
npc:GetSwarmOwner(); -- int
npc:GetSwarmTarget(); -- int
npc:GetWaypointMax(); -- int
npc:IsAnimal(); -- bool
npc:IsGuarding(); -- bool
npc:IsOnHatelist(Lua_Mob ent); -- bool
npc:MerchantCloseShop(); -- void
npc:MerchantOpenShop(); -- void
npc:ModifyNPCStat(const char *stat, const char *value); -- void
npc:MoveTo(float x, float y, float z, float h, bool save); -- void
npc:NextGuardPosition(); -- void
npc:PauseWandering(int pause_time); -- void
npc:PickPocket(Lua_Client thief); -- void
npc:RecalculateSkills(); -- void
npc:RemoveAISpell(int spell_id); -- void
npc:RemoveCash(); -- void
npc:RemoveItem(int item_id); -- void
npc:RemoveItem(int item_id, int quantity); -- void
npc:RemoveItem(int item_id, int quantity, int slot); -- void
npc:ResumeWandering(); -- void
npc:SaveGuardSpot(float x, float y, float z, float heading); -- void
npc:SetCopper(uint32 amt); -- void
npc:SetFollowCanRun(bool v); -- void
npc:SetFollowDistance(int dist); -- void
npc:SetFollowID(int id); -- void
npc:SetGold(uint32 amt); -- void
npc:SetGrid(int grid); -- void
npc:SetNPCFactionID(int id); -- void
npc:SetPetSpellID(int id); -- void
npc:SetPlatinum(uint32 amt); -- void
npc:SetPrimSkill(int skill_id); -- void
npc:SetSaveWaypoint(int wp); -- void
npc:SetSecSkill(int skill_id); -- void
npc:SetSilver(uint32 amt); -- void
npc:SetSimpleRoamBox(float box_size); -- void
npc:SetSimpleRoamBox(float box_size, float move_distance); -- void
npc:SetSimpleRoamBox(float box_size, float move_distance, int move_delay); -- void
npc:SetSp2(int sg2); -- void
npc:SetSpellFocusDMG(int focus); -- void
npc:SetSpellFocusHeal(int focus); -- void
npc:SetSwarmTarget(int target); -- void
npc:SetTaunting(bool t); -- void
npc:SetWaypointPause(); -- void
npc:Signal(int id); -- void
npc:StartSwarmTimer(uint32 duration); -- void
npc:StopWandering(); -- void
npc:UpdateWaypoint(int wp); -- void
```
{% endtab %}
{% endtabs %}

