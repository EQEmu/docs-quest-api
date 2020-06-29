# Doors Manipulation

## Description

This page has everything to do with doors, or rather in game objects and how you can place/manipulate them.

* This plugin allows for developers to manipulate objects and door date real time. And it does it very well. It also has all of the door/object data loaded from every single zone into a Mysql table and allows developers to be very creative about the world customization process
* It has coordinate helpers that you don't need to source into your NPC Types table, but it is recommended, it will show you -X, -Y etc. around the object you are editing.
* The [\`cust\_obj\_data\`](http://wiki.eqemulator.org/l/wa/files/Doors/cust_obj_data.rar) table has EVERY SINGLE model listed all the way through RoF zones? You can go to town listing every single model and click through them instantly, EXTREMELY powerful.

## **Example Videos**

{% embed url="https://youtu.be/uuIMrW7QOzI" %}

{% embed url="https://youtu.be/RLTGpqaTKCQ" %}

## **Requirements**

* **Required:** plugin::LoadMysql\(\);
* **Required:** Mysql table \`cust\_obj\_data\` - 

{% file src="../../.gitbook/assets/cust\_obj\_data \(1\).rar" caption="Required Table SQL" %}

* **Required:** NPC Types ID 51, 52, 53, 54 for the 'Reference NPC's' 

## **Door Helper \(Reference\) NPC's**

{% tabs %}
{% tab title="Query" %}
```sql
REPLACE INTO `npc_types` (`id`, `name`, `lastname`, `level`, `race`, `class`, `bodytype`, `hp`, `mana`, `gender`, `texture`, `helmtexture`, `size`, `hp_regen_rate`, `mana_regen_rate`, `loottable_id`, `merchant_id`, `alt_currency_id`, `npc_spells_id`,
`npc_faction_id`, `adventure_template_id`, `trap_template`, `mindmg`, `maxdmg`, `attack_count`, `npcspecialattks`, `aggroradius`, `face`, `luclin_hairstyle`, `luclin_haircolor`, `luclin_eyecolor`, `luclin_eyecolor2`, `luclin_beardcolor`, `luclin_beard`,
`drakkin_heritage`, `drakkin_tattoo`, `drakkin_details`, `armortint_id`, `armortint_red`, `armortint_green`, `armortint_blue`, `d_meele_texture1`, `d_meele_texture2`, `prim_melee_type`, `sec_melee_type`, `runspeed`, `MR`, `CR`, `DR`, `FR`, `PR`, `Corrup`,
`see_invis`, `see_invis_undead`, `qglobal`, `AC`, `npc_aggro`, `spawn_limit`, `attack_speed`, `findable`, `STR`, `STA`, `DEX`, `AGI`, `_INT`, `WIS`, `CHA`, `see_hide`, `see_improved_hide`, `trackable`, `isbot`, `exclude`, `ATK`, `Accuracy`, `slow_mitigation`,
`version`, `maxlevel`, `scalerate`, `private_corpse`, `unique_spawn_by_name`, `underwater`, `isquest`, `emoteid`) VALUES (51, '-X', NULL, 1, 127, 1, 11, 31, 0, 0, 0, 0, 7, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -1, 'ZiGH', 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 28, 28, 1.25, 0, 0,
0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 75, 75, 75, 75, 80, 75, 75, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 100, 0, 0, 0, 0, 0);
 
REPLACE INTO `npc_types` (`id`, `name`, `lastname`, `level`, `race`, `class`, `bodytype`, `hp`, `mana`, `gender`, `texture`, `helmtexture`, `size`, `hp_regen_rate`, `mana_regen_rate`, `loottable_id`, `merchant_id`, `alt_currency_id`, `npc_spells_id`,
`npc_faction_id`, `adventure_template_id`, `trap_template`, `mindmg`, `maxdmg`, `attack_count`, `npcspecialattks`, `aggroradius`, `face`, `luclin_hairstyle`, `luclin_haircolor`, `luclin_eyecolor`, `luclin_eyecolor2`, `luclin_beardcolor`, `luclin_beard`,
`drakkin_heritage`, `drakkin_tattoo`, `drakkin_details`, `armortint_id`, `armortint_red`, `armortint_green`, `armortint_blue`, `d_meele_texture1`, `d_meele_texture2`, `prim_melee_type`, `sec_melee_type`, `runspeed`, `MR`, `CR`, `DR`, `FR`, `PR`, `Corrup`,
`see_invis`, `see_invis_undead`, `qglobal`, `AC`, `npc_aggro`, `spawn_limit`, `attack_speed`, `findable`, `STR`, `STA`, `DEX`, `AGI`, `_INT`, `WIS`, `CHA`, `see_hide`, `see_improved_hide`, `trackable`, `isbot`, `exclude`, `ATK`, `Accuracy`, `slow_mitigation`,
`version`, `maxlevel`, `scalerate`, `private_corpse`, `unique_spawn_by_name`, `underwater`, `isquest`, `emoteid`) VALUES (52, '+X', NULL, 1, 127, 1, 11, 31, 0, 0, 0, 0, 7, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -1, 'ZiGH', 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 28, 28, 1.25, 0, 0,
 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 75, 75, 75, 75, 80, 75, 75, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 100, 0, 0, 0, 0, 0);
 
REPLACE INTO `npc_types` (`id`, `name`, `lastname`, `level`, `race`, `class`, `bodytype`, `hp`, `mana`, `gender`, `texture`, `helmtexture`, `size`, `hp_regen_rate`, `mana_regen_rate`, `loottable_id`, `merchant_id`, `alt_currency_id`, `npc_spells_id`,
`npc_faction_id`, `adventure_template_id`, `trap_template`, `mindmg`, `maxdmg`, `attack_count`, `npcspecialattks`, `aggroradius`, `face`, `luclin_hairstyle`, `luclin_haircolor`, `luclin_eyecolor`, `luclin_eyecolor2`, `luclin_beardcolor`, `luclin_beard`,
`drakkin_heritage`, `drakkin_tattoo`, `drakkin_details`, `armortint_id`, `armortint_red`, `armortint_green`, `armortint_blue`, `d_meele_texture1`, `d_meele_texture2`, `prim_melee_type`, `sec_melee_type`, `runspeed`, `MR`, `CR`, `DR`, `FR`, `PR`, `Corrup`,
`see_invis`, `see_invis_undead`, `qglobal`, `AC`, `npc_aggro`, `spawn_limit`, `attack_speed`, `findable`, `STR`, `STA`, `DEX`, `AGI`, `_INT`, `WIS`, `CHA`, `see_hide`, `see_improved_hide`, `trackable`, `isbot`, `exclude`, `ATK`, `Accuracy`, `slow_mitigation`,
`version`, `maxlevel`, `scalerate`, `private_corpse`, `unique_spawn_by_name`, `underwater`, `isquest`, `emoteid`) VALUES (53, '-Y', NULL, 1, 127, 1, 11, 31, 0, 0, 0, 0, 7, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -1, 'ZiGH', 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 28, 28, 1.25, 0, 0,
 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 75, 75, 75, 75, 80, 75, 75, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 100, 0, 0, 0, 0, 0);
 
REPLACE INTO `npc_types` (`id`, `name`, `lastname`, `level`, `race`, `class`, `bodytype`, `hp`, `mana`, `gender`, `texture`, `helmtexture`, `size`, `hp_regen_rate`, `mana_regen_rate`, `loottable_id`, `merchant_id`, `alt_currency_id`, `npc_spells_id`,
`npc_faction_id`, `adventure_template_id`, `trap_template`, `mindmg`, `maxdmg`, `attack_count`, `npcspecialattks`, `aggroradius`, `face`, `luclin_hairstyle`, `luclin_haircolor`, `luclin_eyecolor`, `luclin_eyecolor2`, `luclin_beardcolor`, `luclin_beard`,
`drakkin_heritage`, `drakkin_tattoo`, `drakkin_details`, `armortint_id`, `armortint_red`, `armortint_green`, `armortint_blue`, `d_meele_texture1`, `d_meele_texture2`, `prim_melee_type`, `sec_melee_type`, `runspeed`, `MR`, `CR`, `DR`, `FR`, `PR`, `Corrup`,
`see_invis`, `see_invis_undead`, `qglobal`, `AC`, `npc_aggro`, `spawn_limit`, `attack_speed`, `findable`, `STR`, `STA`, `DEX`, `AGI`, `_INT`, `WIS`, `CHA`, `see_hide`, `see_improved_hide`, `trackable`, `isbot`, `exclude`, `ATK`, `Accuracy`, `slow_mitigation`,
`version`, `maxlevel`, `scalerate`, `private_corpse`, `unique_spawn_by_name`, `underwater`, `isquest`, `emoteid`) VALUES (54, '+Y', NULL, 1, 127, 1, 11, 31, 0, 0, 0, 0, 7, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -1, 'ZiGH', 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 28, 28, 1.25, 0, 0,
0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 75, 75, 75, 75, 80, 75, 75, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 100, 0, 0, 0, 0, 0);
```
{% endtab %}
{% endtabs %}

* Whenever you have a door highlighted \(Clicking it\) it in game with the below code, you can type \#door, to also use manipulation commands...

## Activating this Plugin

* Pull down door\_plugin.pl from the [Github repository](https://github.com/ProjectEQ/projecteqquests/blob/master/plugins/Doors_Manip.pl).
* Include the code below in your subroutines

{% tabs %}
{% tab title="Perl" %}
```perl
sub EVENT_CLICKDOOR {
    if($status > 200) {
        plugin::Doors_Manipulation_EVENT_CLICKDOOR(); # Door Manipulation Plugin
    }
}
 
sub EVENT_SAY {
    if($status > 200) {
        plugin::Doors_Manipulation_EVENT_SAY(); # Door Manipulation Plugin
    }
}
```
{% endtab %}
{% endtabs %}

