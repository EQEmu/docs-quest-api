# Door Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$door->GetDoorDBID()
$door->GetDoorID()
$door->GetHeading()
$door->GetID()
$door->GetIncline()
$door->GetIncline()
$door->GetKeyItem()
$door->GetLockpick()
$door->GetModelName()
$door->GetNoKeyring(uint8 type)
$door->GetOpenType()
$door->GetX()
$door->GetY()
$door->GetZ()
$door->InsertDoor()
$door->SetHeading(float heading)
$door->SetIncline(uint32 incline)
$door->SetKeyItem(uint32 key_item_id)
$door->SetLocation(float x, float y, float z)
$door->SetLockpick(uint32 lockpick_type)
$door->SetModelName(string name)
$door->SetNoKeyring(uint8 no_key_ring)
$door->SetOpenType(uint32 open_type)
$door->SetSize(uint32 size)
$door->SetX(float x)
$door->SetY(float y)
$door->SetZ(float z)
```
{% endtab %}

{% tab title="Lua" %}
```lua
door:CreateDatabaseEntry(); -- void
door:ForceClose(Lua_Mob sender); -- void
door:ForceClose(Lua_Mob sender, bool alt_mode); -- void
door:ForceOpen(Lua_Mob sender); -- void
door:ForceOpen(Lua_Mob sender, bool alt_mode); -- void
door:GetDisableTimer(); -- bool
door:GetDoorDBID(); -- uint32
door:GetDoorID(); -- uint32
door:GetHeading(); -- float
door:GetIncline(); -- uint32
door:GetKeyItem(); -- uint32
door:GetLockPick(); -- uint32
door:GetNoKeyring(); -- int
door:GetOpenType(); -- uint32
door:GetSize(); -- uint32
door:GetX(); -- float
door:GetY(); -- float
door:GetZ(); -- float
door:SetDisableTimer(bool flag); -- void
door:SetDoorName(const char *name); -- void
door:SetHeading(float h); -- void
door:SetIncline(uint32 incline); -- void
door:SetKeyItem(uint32 key); -- void
door:SetLocation(float x, float y, float z); -- void
door:SetLockPick(uint32 pick); -- void
door:SetNoKeyring(int type); -- void
door:SetOpenType(uint32 type); -- void
door:SetSize(uint32 sz); -- void
door:SetX(float x); -- void
door:SetY(float y); -- void
door:SetZ(float z); -- void
```
{% endtab %}
{% endtabs %}

