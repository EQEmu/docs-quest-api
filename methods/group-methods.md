# Group Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$group->CastGroupSpell(mob* caster, uint16 spell_id)
$group->DisbandGroup()
$group->GetHighestLevel()
$group->GetID()
$group->GetLeader()
$group->GetLeaderName()
$group->GetMember(int group_index)
$group->GetTotalGroupDamage(mob* other)
$group->GroupCount()
$group->GroupMessage(mob* sender, uint8 language, string message)
$group->IsGroupMember(client)
$group->IsLeader(mob* target)
$group->SendHPPacketsFrom(mob* new_member)
$group->SendHPPacketsTo(mob* new_member)
$group->SetLeader(mob* new_leader)
$group->SplitExp(uint32 exp, mob* other)
$group->SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum)
$group->TeleportGroup(mob* sender, uint32 zone_id, float x, float y, float z, float heading)
```
{% endtab %}

{% tab title="Lua" %}
```
group:CastGroupSpell(Lua_Mob caster, int spell_id); -- void
```

```lua
group:DisbandGroup(); -- void
group:GetHighestLevel(); -- int
group:GetID(); -- int
group:GetLeader(); -- Lua_Mob
group:GetLowestLevel(); -- int
group:GetMember(int index); -- Lua_Mob
group:GetTotalGroupDamage(Lua_Mob other); -- uint32
group:GroupCount(); -- int
group:GroupMessage(Lua_Mob sender, int language, const char *message); -- void
group:IsGroupMember(Lua_Mob mob); -- bool
group:IsLeader(Lua_Mob leader); -- bool
group:SetLeader(Lua_Mob leader); -- void
group:SplitExp(uint32 exp, Lua_Mob other); -- void
group:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
group:SplitMoney(uint32 copper, uint32 silver, uint32 gold, uint32 platinum, Lua_Client splitter); -- void
group:TeleportGroup(Lua_Mob sender, uint32 zone_id, uint32 instance_id, float x, float y, float z, float h); -- void
```
{% endtab %}
{% endtabs %}

