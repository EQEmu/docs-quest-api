# Hate Entry Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$hate_entry->GetDamage();
$hate_entry->GetData();
$hate_entry->GetHate();
```
{% endtab %}

{% tab title="Lua" %}
```lua
hate_entry:GetDamage(); -- int
hate_entry:GetEnt(); -- Lua_Mob
hate_entry:GetFrenzy(); -- int
hate_entry:GetHate(); -- int
hate_entry:SetDamage(int value); -- void
hate_entry:SetEnt(Lua_Mob e); -- void
hate_entry:SetFrenzy(bool value); -- void
hate_entry:SetHate(int value); -- void
```
{% endtab %}
{% endtabs %}

