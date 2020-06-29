# Object Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$object->ClearUser()
$object->Close()
$object->Delete([bool reset_state = false])
$object->DeleteItem(uint8 index)
$object->Depop()
$object->EntityVariableExists(string key)
$object->GetDBID()
$object->GetEntityVariable(string key)
$object->GetHeading()
$object->GetID()
$object->GetIcon()
$object->GetItemID()
$object->GetModelName()
$object->GetSize()
$object->GetSize()
$object->GetSize()
$object->GetSolidType()
$object->GetType()
$object->GetX()
$object->GetY()
$object->GetZ()
$object->IsGroundSpawn()
$object->IsObject()
$object->Repop()
$object->Save()
$object->SetEntityVariable(string key, string var)
$object->SetHeading(float heading)
$object->SetID(uint16 id)
$object->SetIcon(uint32 icon)
$object->SetItemID(uint32 item_id)
$object->SetLocation(float x, float y, float z)
$object->SetModelName(string name)
$object->SetSize(float size)
$object->SetSolidType(uint16 type)
$object->SetTiltX(float tilt_x)
$object->SetTiltY(float tilt_y)
$object->SetType(uint32 type)
$object->SetX(float X)
$object->SetY(float Y)
$object->SetZ(float Z)
$object->StartDecay()
$object->VarSave()
```
{% endtab %}

{% tab title="Lua" %}
```lua
object:ClearUser(); -- void
object:Close(); -- void
object:Delete(); -- void
object:Delete(bool reset_state); -- void
object:DeleteItem(int index); -- void
object:Depop(); -- void
object:EntityVariableExists(const char *name); -- bool
object:GetDBID(); -- uint32
object:GetHeading(); -- float
object:GetID(); -- int
object:GetIcon(); -- uint32
object:GetItemID(); -- uint32
object:GetType(); -- uint32
object:GetX(); -- float
object:GetY(); -- float
object:GetZ(); -- float
object:IsGroundSpawn(); -- bool
object:Repop(); -- void
object:Save(); -- bool
object:SetEntityVariable(const char *name, const char *value); -- void
object:SetHeading(float h); -- void
object:SetID(int user); -- void
object:SetIcon(uint32 icon); -- void
object:SetItemID(uint32 item_id); -- void
object:SetLocation(float x, float y, float z); -- void
object:SetModelName(const char *name); -- void
object:SetType(uint32 type); -- void
object:SetX(float x); -- void
object:SetY(float y); -- void
object:SetZ(float z); -- void
object:StartDecay(); -- void
object:VarSave(); -- uint32
```
{% endtab %}
{% endtabs %}

