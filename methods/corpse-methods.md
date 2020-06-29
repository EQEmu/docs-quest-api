# Corpse Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$corpse->AddItem(uint32 item_id, uint16 charges, [unt16 slot = 0])
$corpse->AddLooter(mob* who)
$corpse->AllowMobLoot(mob* them, uint8 slot)
$corpse->CanMobLoot(int character_id)
$corpse->CastRezz(uint16 spell_id, [mob* caster = nullptr])
$corpse->CompleteRezz()
$corpse->CountItems()
$corpse->Delete()
$corpse->GetCharID()
$corpse->GetCopper()
$corpse->GetDBID()
$corpse->GetDecayTime()
$corpse->GetGold()
$corpse->GetOwnerName()
$corpse->GetPlatinum()
$corpse->GetSilver()
$corpse->GetWornItem(equipslot)
$corpse->IsEmpty()
$corpse->IsLocked()
$corpse->IsRezzed()
$corpse->Lock()
$corpse->RemoveCash()
$corpse->RemoveItem(uint16 loot_slot)
$corpse->ResetLooter()
$corpse->SetCash(uint16 copper, uint16 silver, uint16 gold, uint16 platinum)
$corpse->SetDecayTimer(uint32 decay_time)
$corpse->Summon(client* client, bool is_spell)
$corpse->UnLock()
```
{% endtab %}

{% tab title="Lua" %}
```lua
corpse:AddItem(uint32 itemnum, uint16 charges, int16 slot, uint32 aug1, uint32 aug2, uint32 aug3, uint32 aug4, uint32 aug5); -- void
corpse:AddLooter(Lua_Mob who); -- void
corpse:AllowMobLoot(Lua_Mob them, uint8 slot); -- void
corpse:Bury(); -- void
corpse:CanMobLoot(int charid); -- bool
corpse:CountItems(); -- uint32
corpse:Delete(); -- void
corpse:Depop(); -- void
corpse:GetCharID(); -- uint32
corpse:GetCopper(); -- uint32
corpse:GetDBID(); -- uint32
corpse:GetDecayTime(); -- uint32
corpse:GetGold(); -- uint32
corpse:GetPlatinum(); -- uint32
corpse:GetSilver(); -- uint32
corpse:GetWornItem(int16 equipSlot); -- uint32
corpse:IsEmpty(); -- bool
corpse:IsLocked(); -- bool
corpse:IsRezzed(); -- bool
corpse:Lock(); -- void
corpse:RemoveCash(); -- void
corpse:RemoveItem(uint16 lootslot); -- void
corpse:ResetLooter(); -- void
corpse:Save(); -- bool
corpse:SetCash(uint32 copper, uint32 silver, uint32 gold, uint32 platinum); -- void
corpse:SetDecayTimer(uint32 decaytime); -- void
corpse:Summon(Lua_Client client, bool spell, bool checkdistance); -- bool
corpse:UnLock(); -- void
```
{% endtab %}
{% endtabs %}

