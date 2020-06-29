# Spawn Methods \(Lua\)

{% tabs %}
{% tab title="Lua" %}
```lua
spawn:CurrentNPCID(); -- uint32
spawn:Depop(); -- void
spawn:Disable(); -- void
spawn:Enable(); -- void
spawn:Enabled(); -- bool
spawn:ForceDespawn(); -- void
spawn:GetHeading(); -- float
spawn:GetID(); -- uint32
spawn:GetKillCount(); -- uint32
spawn:GetSpawnCondition(); -- uint32
spawn:GetVariance(); -- uint32
spawn:GetX(); -- float
spawn:GetY(); -- float
spawn:GetZ(); -- float
spawn:LoadGrid(); -- void
spawn:NPCPointerValid(); -- bool
spawn:Repop(); -- void
spawn:Repop(uint32 delay); -- void
spawn:Reset(); -- void
spawn:RespawnTimer(); -- uint32
spawn:SetCurrentNPCID(uint32 nid); -- void
spawn:SetNPCPointer(Lua_NPC n); -- void
spawn:SetRespawnTimer(uint32 newrespawntime); -- void
spawn:SetTimer(uint32 duration); -- void
spawn:SetVariance(uint32 newvariance); -- void
spawn:SpawnGroupID(); -- uint32
```
{% endtab %}
{% endtabs %}

