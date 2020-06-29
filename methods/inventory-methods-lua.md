# Inventory Methods \(Lua\)

{% tabs %}
{% tab title="Lua" %}
```lua
inventory:CalcBagIdx(int slot_id); -- int
inventory:CalcMaterialFromSlot(int equipslot); -- int
inventory:CalcSlotFromMaterial(int material); -- int
inventory:CalcSlotId(int slot_id); -- int
inventory:CalcSlotId(int slot_id, int bag_slot); -- int
inventory:CanItemFitInContainer(Lua_Item item, Lua_Item container); -- bool
inventory:CheckNoDrop(int slot_id); -- bool
inventory:DeleteItem(int slot_id); -- bool
inventory:DeleteItem(int slot_id, int quantity); -- bool
inventory:FindFreeSlot(bool for_bag, bool try_cursor); -- int
inventory:FindFreeSlot(bool for_bag, bool try_cursor, int min_size); -- int
inventory:FindFreeSlot(bool for_bag, bool try_cursor, int min_size, bool is_arrow); -- int
inventory:GetItem(int slot_id); -- Lua_ItemInst
inventory:GetItem(int slot_id, int bag_slot); -- Lua_ItemInst
inventory:GetSlotByItemInst(Lua_ItemInst inst); -- int
inventory:HasItem(int item_id); -- int
inventory:HasItem(int item_id, int quantity); -- int
inventory:HasItem(int item_id, int quantity, int where); -- int
inventory:HasItemByLoreGroup(uint32 loregroup); -- int
inventory:HasItemByLoreGroup(uint32 loregroup, int where); -- int
inventory:HasItemByUse(int use); -- int
inventory:HasItemByUse(int use, uint8 quantity); -- int
inventory:HasItemByUse(int use, uint8 quantity, uint8 where); -- int
inventory:HasSpaceForItem(Lua_Item item, int quantity); -- bool
inventory:PopItem(int slot_id); -- Lua_ItemInst
inventory:PushCursor(Lua_ItemInst item); -- int
inventory:PutItem(int slot_id, Lua_ItemInst item); -- int
inventory:SupportsContainers(int slot_id); -- bool
inventory:SwapItem(int source_slot, int destination_slot); -- bool
```
{% endtab %}
{% endtabs %}

