# Packet Methods \(Lua\)

{% tabs %}
{% tab title="Lua" %}
```lua
packet:GetOpcode(); -- int
packet:GetRawOpcode(); -- int
packet:GetSize(); -- int
packet:Lua_Packet(const Lua_Packet& o); -- Lua_Packet::Lua_Packet(const
packet:ReadDouble(int offset); -- double
packet:ReadFixedLengthString(int offset, int string_length); -- std::string
packet:ReadFloat(int offset); -- float
packet:ReadInt16(int offset); -- int
packet:ReadInt32(int offset); -- int
packet:ReadInt64(int offset); -- int64
packet:ReadInt8(int offset); -- int
packet:ReadString(int offset); -- std::string
packet:SetOpcode(int op); -- void
packet:SetRawOpcode(int op); -- void
packet:WriteDouble(int offset, double value); -- void
packet:WriteFixedLengthString(int offset, std::string value, int string_length); -- void
packet:WriteFloat(int offset, float value); -- void
packet:WriteInt16(int offset, int value); -- void
packet:WriteInt32(int offset, int value); -- void
packet:WriteInt64(int offset, int64 value); -- void
packet:WriteInt8(int offset, int value); -- void
packet:WriteString(int offset, std::string value); -- void
packet:operator=(const Lua_Packet& o); -- Lua_Packet&
```
{% endtab %}
{% endtabs %}

