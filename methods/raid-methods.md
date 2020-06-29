# Raid Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$raid->BalanceHP(int32 penalty, uint32 group_id)
$raid->CastGroupSpell(mob* caster, uint16 spell_id, uint32 group_id)
$raid->GetClientByIndex(uint16 raid_indez)
$raid->GetGroup(string name)
$raid->GetHighestLevel()
$raid->GetID()
$raid->GetLowestLevel()
$raid->GetMember(int raid_index)
$raid->GetTotalRaidDamage([mob* other = nullptr])
$raid->GroupCount(uint32 group_id)
$raid->IsGroupLeader(string name)
$raid->IsLeader(string name)
$raid->IsRaidMember(string name)
$raid->RaidCount()
$raid->SplitExp(uint32 experience, [mob* other = nullptr])
$raid->SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum)
$raid->TeleportGroup(mob* sender, uint32 zone_id, float X, float Y, float Z, float heading, uint32 group_id)
$raid->TeleportRaid(mob* sender, uint32 zone_id, float X, float Y, float Z, float heading)
```
{% endtab %}

{% tab title="Lua" %}
```lua
raid:BalanceHP(int penalty, uint32 group_id); -- void
raid:CastGroupSpell(Lua_Mob caster, int spell_id, uint32 group_id); -- void
raid:GetClientByIndex(int index); -- Lua_Client
raid:GetGroup(Lua_Client c); -- int
raid:GetGroup(const char *c); -- int
raid:GetGroupNumber(int index); -- int
raid:GetHighestLevel(); -- int
raid:GetID(); -- int
raid:GetLowestLevel(); -- int
raid:GetMember(int index); -- Lua_Client
raid:GetTotalRaidDamage(Lua_Mob other); -- uint32
raid:GroupCount(uint32 group_id); -- int
raid:IsGroupLeader(const char *name); -- bool
raid:IsLeader(Lua_Client c); -- bool
raid:IsLeader(const char *c); -- bool
raid:IsRaidMember(const char *name); -- bool
raid:RaidCount(); -- int
raid:SplitExp(uint32 exp, Lua_Mob other); -- void
raid:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
raid:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, Lua_Client splitter); -- void
raid:TeleportGroup(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h, uint32 group_id); -- void
raid:TeleportRaid(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h); -- void
```
{% endtab %}
{% endtabs %}

