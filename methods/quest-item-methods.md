# Quest Item Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$quest_item->GetAugment(int16 slot_id)
$quest_item->GetCharges()
$quest_item->GetID()
$quest_item->GetName()
$quest_item->IsAttuned()
$quest_item->IsType(type)
$quest_item->ItemSay(string text [int language_id])
$quest_item->SetScale(float scale_multiplier)
```
{% endtab %}

{% tab title="Lua" %}
```lua
iteminst:AddExp(uint32 exp); -- void
iteminst:ClearTimers(); -- void
iteminst:Clone(); -- Lua_ItemInst
iteminst:DeleteCustomData(std::string identifier); -- void
iteminst:GetAugment(int slot); -- Lua_ItemInst
iteminst:GetAugmentItemID(int slot); -- uint32
iteminst:GetAugmentType(); -- int
iteminst:GetCharges(); -- int
iteminst:GetColor(); -- uint32
iteminst:GetCustomData(std::string identifier); -- std::string
iteminst:GetCustomDataString(); -- std::string
iteminst:GetExp(); -- uint32
iteminst:GetID(); -- uint32
iteminst:GetItem(); -- Lua_Item
iteminst:GetItem(int slot); -- Lua_ItemInst
iteminst:GetItemID(int slot); -- uint32
iteminst:GetItemScriptID(); -- uint32
iteminst:GetKillsNeeded(int current_level); -- uint32
iteminst:GetMaxEvolveLvl(); -- int
iteminst:GetPrice(); -- uint32
iteminst:GetTotalItemCount(); -- int
iteminst:GetUnscaledItem(int slot); -- Lua_Item
iteminst:IsAmmo(); -- bool
iteminst:IsAugmentable(); -- bool
iteminst:IsAugmented(); -- bool
iteminst:IsEquipable(int race, int class_); -- bool
iteminst:IsEquipable(int slot_id); -- bool
iteminst:IsExpendable(); -- bool
iteminst:IsInstNoDrop(); -- bool
iteminst:IsStackable(); -- bool
iteminst:IsType(int item_class); -- bool
iteminst:IsWeapon(); -- bool
iteminst:Lua_ItemInst(const Lua_ItemInst& o); -- Lua_ItemInst::Lua_ItemInst(const
iteminst:SetCharges(int charges); -- void
iteminst:SetColor(uint32 color); -- void
iteminst:SetCustomData(std::string identifier, bool value); -- void
iteminst:SetCustomData(std::string identifier, float value); -- void
iteminst:SetCustomData(std::string identifier, int value); -- void
iteminst:SetCustomData(std::string identifier, std::string value); -- void
iteminst:SetExp(uint32 exp); -- void
iteminst:SetInstNoDrop(bool flag); -- void
iteminst:SetPrice(uint32 price); -- void
iteminst:SetScale(double scale_factor); -- void
iteminst:SetScaling(bool v); -- void
iteminst:SetTimer(std::string name, uint32 time); -- void
iteminst:StopTimer(std::string name); -- void
iteminst:operator=(const Lua_ItemInst& o); -- Lua_ItemInst&
```
{% endtab %}
{% endtabs %}

