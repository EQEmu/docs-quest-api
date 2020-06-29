# Mob Methods

{% tabs %}
{% tab title="Perl" %}
```perl
$mob->AddFeignMemory(client* attacker)
$mob->AddToHateList(mob* other, [int32 hate = 0], [int32 damage = 0], [bool yell_for_help = true], [bool frenzy = false], [bool buff_tic = false])
$mob->Attack(mob* other, [int hand = 13 [prim|sec]], [bool from_riposte = false])
$mob->BehindMob(mob* other = 0, [float X = 0.0f], [float Y= 0.0f])
$mob->BuffCount()
$mob->BuffFadeAll()
$mob->BuffFadeByEffect(int effect_id, int skip_slot = -1)
$mob->BuffFadeBySlot(int slot, bool recalc_bonuses = true)
$mob->BuffFadeBySpellID(uint16 spell_id)
$mob->CalculateDistance(float X, float Y, float Z)
$mob->CalculateHeadingToTarget(float X, float Y)
$mob->CameraEffect(uint32 duration, [uint32 intensity = 0], [client* single_client = nullptr], [bool is_world_wide = false])
$mob->CanBuffStack(uint16 spell_id, uint8 caster_level, [bool fail_if_overwritten = false])
$mob->CanClassEquipItem(uint32 item_id)
$mob->CanThisClassDodge()
$mob->CanThisClassDoubleAttack()
$mob->CanThisClassDualWield()
$mob->CanThisClassParry()
$mob->CanThisClassRiposte()
$mob->CastSpell(uint16 spell_id, uint16 target_id, [int slot = 22], [int32 cast_time = -1], [int32 mana_cost = -1], [int16 resist_adjust = 0])
$mob->CastToClient()
$mob->CastToCorpse()
$mob->CastToMob()
$mob->CastToNPC()
$mob->CastingSpellID()
$mob->ChangeSize(float in_size, [bool no_restriction = false])
$mob->Charmed()
$mob->CheckAggro(mob* other)
$mob->CheckAggroAmount(uint16 spell_id)
$mob->CheckHealAggroAmount(uint16 spell_id, uint32 possible_heal_amt)
$mob->CheckLoS(mob*)
$mob->CheckLoSToLoc(float X, float Y, float Z, float mob_size)
$mob->ClearFeignMemory()
$mob->ClearSpecialAbilities()
$mob->CombatRange(mob* target)
$mob->Damage(mob* from, int32 damage, uint16 spell_id, int attack_skill, [bool avoidable = true], [int8 buffslot = -1], [bool buff_tic = false])
$mob->Depop(startspawntimer = true)
$mob->DivineAura()
$mob->DoAnim(int animation_number, [int type = 0])
$mob->DoArcheryAttackDmg(mob* target, [range_weapon_item_instance = nullptr], [ammo_item_instance = nullptr], uint16 weapon_damage, int16 chance_mod, int16 focus)
$mob->DoKnockback(mob* caster, uint32 push_back_amount, uint32 push_up_amount)
$mob->DoMeleeSkillAttackDmg(mob* target, uint16 weapon_damage, int skill, int16 chance_mod, int16 focus, uint8 can_riposte)
$mob->DoSpecialAttackDamage(mob* target, int skill, int32 max_damage, [int32 min_damage = 1], [int32 hate_override = -11])
$mob->DoThrowingAttackDmg(mob* target, [range_weapon_item_instance = nullptr], [ammo_item_instance = nullptr], uint16 weapon_damage, int16 chance_mod, int16 focus)
$mob->DontBuffMeBefore()
$mob->DontDotMeBefore()
$mob->DontHealMeBefore()
$mob->DontRootMeBefore()
$mob->DontSnareMeBefore()
$mob->DoubleAggro(mob* other)
$mob->Emote(string message)
$mob->EntityVariableExists(string id)
$mob->FaceTarget([mob* target = 0])
$mob->FindBuff(uint16 spell_id)
$mob->FindBuffBySlot(int slot)
$mob->FindGroundZ(float X, float Y, float Z_offset)
$mob->FindType(uint8 type, [bool offensive = false], [uint16 threshold = 100])
$mob->GMMove(float X, float Y, float Z, [float heading = 0.01])
$mob->Gate()
$mob->GetAA(uint32 rank_id)
$mob->GetAAByAAID(uint32 aa_id)
$mob->GetAC()
$mob->GetAGI()
$mob->GetATK()
$mob->GetActSpellCasttime(uint16 spell_id, uint32 cast_time)
$mob->GetActSpellCost(uint16 spell_id, int32 cost)
$mob->GetActSpellDamage(uint16 spell_id, int32 value)
$mob->GetActSpellDuration(uint16 spell_id, int32 duration)
$mob->GetActSpellHealing(uint16 spell_id, int32 value)
$mob->GetActSpellRange(uint16 spell_id, float range)
$mob->GetAggroRange()
$mob->GetAllowBeneficial()
$mob->GetAppearance()
$mob->GetArmorTint(uint8 material_slot)
$mob->GetAssistRange()
$mob->GetBaseGender()
$mob->GetBaseRace()
$mob->GetBaseSize()
$mob->GetBeard()
$mob->GetBeardColor()
$mob->GetBodyType()
$mob->GetBuffSlotFromType(uint16 type)
$mob->GetCHA()
$mob->GetCR()
$mob->GetCasterLevel(spell_id)
$mob->GetClass()
$mob->GetClassLevelFactor()
$mob->GetCleanName()
$mob->GetCorruption()
$mob->GetDEX()
$mob->GetDR()
$mob->GetDamageAmount(mob* target_mob)
$mob->GetDeity()
$mob->GetDrakkinDetails()
$mob->GetDrakkinHeritage()
$mob->GetDrakkinTattoo()
$mob->GetEntityVariable(string id)
$mob->GetEquipment(uint8 material_slot)
$mob->GetEquipmentColor(uint8 material_slot)
$mob->GetEquipmentMaterial(uint8 material_slot)
$mob->GetEyeColor1()
$mob->GetEyeColor2()
$mob->GetFR()
$mob->GetFlurryChance()
$mob->GetFollowID()
$mob->GetGender()
$mob->GetHP()
$mob->GetHPRatio()
$mob->GetHairColor()
$mob->GetHairStyle()
$mob->GetHandToHandDamage()
$mob->GetHandToHandDelay()
$mob->GetHaste()
$mob->GetHateAmount(mob* mob, [bool is_damage = false])
$mob->GetHateDamageTop(mob* other)
$mob->GetHateList()
$mob->GetHateRandom()
$mob->GetHateTop()
$mob->GetHeading()
$mob->GetHelmTexture()
$mob->GetHerosForgeModel(uint8 material_slot)
$mob->GetID()
$mob->GetINT()
$mob->GetInvul()
$mob->GetItemHPBonuses()
$mob->GetItemStat(uint32 item_id, string stat)
$mob->GetLevel()
$mob->GetLevelCon(uint8 other_level)
$mob->GetLevelHP(uint8 level)
$mob->GetLuclinFace()
$mob->GetMR()
$mob->GetMana()
$mob->GetManaRatio()
$mob->GetMaxAGI()
$mob->GetMaxCHA()
$mob->GetMaxDEX()
$mob->GetMaxHP()
$mob->GetMaxINT()
$mob->GetMaxMana()
$mob->GetMaxSTA()
$mob->GetMaxSTR()
$mob->GetMaxWIS()
$mob->GetMeleeMitigation()
$mob->GetModSkillDmgTaken(int skill_id)
$mob->GetModVulnerability(uint8 resist)
$mob->GetNPCTypeID()
$mob->GetName()
$mob->GetNimbusEffect1()
$mob->GetNimbusEffect2()
$mob->GetNimbusEffect3()
$mob->GetOwnerID()
$mob->GetPR()
$mob->GetPetID()
$mob->GetPetOrder()
$mob->GetPetType()
$mob->GetPhR()
$mob->GetRace()
$mob->GetResist(type)
$mob->GetReverseFactionCon(iother)
$mob->GetRunAnimSpeed()
$mob->GetRunspeed()
$mob->GetSTA()
$mob->GetSTR()
$mob->GetShieldTarget()
$mob->GetSize()
$mob->GetSkill(int skill_id)
$mob->GetSkillDmgTaken(int skill_id)
$mob->GetSpecialAbility(int special_ability)
$mob->GetSpecialAbilityParam(int special_ability, int param)
$mob->GetSpecializeSkillValue(uint16 spell_id)
$mob->GetSpellHPBonuses()
$mob->GetSpellIDFromSlot(slot)
$mob->GetSpellStat(uint32 spell_id, string stat, uint8 slot)
$mob->GetTarget()
$mob->GetTexture()
$mob->GetWIS()
$mob->GetWalkspeed()
$mob->GetWaypointH()
$mob->GetWaypointID()
$mob->GetWaypointPause()
$mob->GetWaypointX()
$mob->GetWaypointY()
$mob->GetWaypointZ()
$mob->GetX()
$mob->GetY()
$mob->GetZ()
$mob->GetZoneID()
$mob->GoToBind()
$mob->HalveAggro(mob* other)
$mob->HasNPCSpecialAtk(string ability_string)
$mob->HasOwner()
$mob->HasPet()
$mob->HasProcs()
$mob->HasShieldEquiped()
$mob->HasTwoHandBluntEquiped()
$mob->HasTwoHanderEquipped()
$mob->HateSummon()
$mob->Heal()
$mob->HealDamage(int32 amount, [mob* caster = 0])
$mob->InterruptSpell([uint16 spell_id = 0xffff])
$mob->IsAIControlled()
$mob->IsAmnesiad()
$mob->IsBeacon()
$mob->IsBeneficialAllowed(mob* target)
$mob->IsBlind()
$mob->IsBot()
$mob->IsCasting()
$mob->IsClient()
$mob->IsCorpse()
$mob->IsDoor()
$mob->IsEliteMaterialItem(uint8 material_slot)
$mob->IsEngaged()
$mob->IsEnraged()
$mob->IsFeared()
$mob->IsImmuneToSpell(uint16 spell_id, [mob* caster = nullptr])
$mob->IsInvisible([mob* other = 0])
$mob->IsMeleeDisabled()
$mob->IsMezzed()
$mob->IsMob()
$mob->IsMoving()
$mob->IsNPC()
$mob->IsNPCCorpse()
$mob->IsObject()
$mob->IsPet()
$mob->IsPlayerCorpse()
$mob->IsRoamer()
$mob->IsRooted()
$mob->IsRunning()
$mob->IsSilenced()
$mob->IsStunned()
$mob->IsTargetable()
$mob->IsTargeted()
$mob->IsTrap()
$mob->IsWarriorClass()
$mob->Kill()
$mob->MakePet(uint16 spell_id, string pet_type, [string name = nullptr])
$mob->MakeTempPet(uint16 spell_id, [string name = nullptr], [uint32 duration = 0], [mob* target = nullptr], [bool sticktarg = 0])
$mob->Mesmerize()
$mob->Message(uint32 emote_color_type, string message)
$mob->Message_StringID(uint32 emote_color_type, uint32 string_id, [uint32 distance = 0])
$mob->ModSkillDmgTaken(int skill, int16 value)
$mob->ModVulnerability(uint8 resist, int16 value)
$mob->NPCSpecialAttacks(string abilities_string, int perm_tag, [bool reset = true], [bool remove = true])
$mob->NavigateTo(float X, float Y, float Z)
$mob->ProcessSpecialAbilities(string str)
$mob->ProjectileAnim(mob* mob, int item_id, [bool is_arrow = false], [float speed = 0], [float angle = 0], [float tilt = 0], [float arc = 0])
$mob->RandomizeFeatures(bool send_illusion, set_variables)
$mob->RangedAttack(mob* other)
$mob->RemoveFromFeignMemory(client* attacker)
$mob->RemoveNimbusEffect(int32 effect_id)
$mob->ResistSpell(uint8 resist_type, uint16 spell_id, [mob* caster = nullptr])
$mob->RogueAssassinate(other)
$mob->Say(string message)
$mob->SeeHide()
$mob->SeeImprovedHide()
$mob->SeeInvisible()
$mob->SeeInvisibleUndead()
$mob->SendAppearanceEffect(int32 param_1, [int32 param_2 = 0], [int32 param_3 = 0], [int32 param_4 = 0], [int32 param_5 = 0], [client* single_client_to_send_to = null])
$mob->SendIllusion(uint16 race, [uint8 gender = 0xff], [uint8 texture  face = 0xff], [uint8 hairstyle = 0xff], [uint8 hair_color = 0xff], [uint8 beard = 0xff], [uint8 beard_color =ff], [uint32 drakkin_tattoo = 0xffffffff], [uint32 drakkin_details = 0xffffffff], [float size = -1])
$mob->SendTo(float new_x, float new_y, float new_z)
$mob->SendToFixZ(float new_x, float new_y, float new_z)
$mob->SendWearChange(uint8 material_slot)
$mob->SetAA(int aa_id, int points, [int charges = 0])
$mob->SetAllowBeneficial(bool value)
$mob->SetAppearance(int appearance [0|1|2|3|4], [ignore_self = true])
$mob->SetBodyType(int32 type, [bool overwrite_orig = false])
$mob->SetCurrentWP(waypoint)
$mob->SetDeltas(float delta_x, float delta_y, float delta_z, float delta_h)
$mob->SetDisableMelee(bool value)
$mob->SetEntityVariable(string id, string var)
$mob->SetExtraHaste(int haste)
$mob->SetFlurryChance(uint8 value)
$mob->SetFlyMode(uint8 flymode[0|1|2|3|4|5])
$mob->SetFollowID(id)
$mob->SetGender(int32 gender)
$mob->SetHP(int32 hp)
$mob->SetHate(mob* other, [int32 hate = 0], [int32 damage = 0])
$mob->SetHeading(float heading)
$mob->SetInvisible(uint8 state)
$mob->SetInvul(bool set_invulnerable)
$mob->SetLD(bool value)
$mob->SetLevel(uint8 in_level, [bool command = false])
$mob->SetMana(amount)
$mob->SetMaxHP()
$mob->SetOOCRegen(int32 new_ooc_regen)
$mob->SetOwnerID(uint16 new_owner_id)
$mob->SetPetID(uint16 new_pet_id)
$mob->SetPetOrder(i)
$mob->SetRace(int32 race)
$mob->SetRunAnimSpeed(int8 speed)
$mob->SetRunning(bool value)
$mob->SetShieldTarget(mob)
$mob->SetSlotTint(uint8 material_slot, uint8 red_tint, uint8 green_tint, uint8 blue_tint)
$mob->SetSpecialAbility(int ability, int value)
$mob->SetSpecialAbilityParam(int ability, int param, int value)
$mob->SetTarget(mob)
$mob->SetTargetable(bool targetable)
$mob->SetTexture(int32 texture)
$mob->Shout(string message)
$mob->SignalClient(client* client, uint32 data)
$mob->SpellEffect(uint32 effect, [uint32 duration = 5000], [uint32 finish_delay = 0], [bool zone_wide = false], [uint32 unk20 = 3000], [bool perm_effect = false], [client* single_client])
$mob->SpellFinished(uint16 spell_id, [mob* spell_target = this], [uint16 mana_cost = 0], [uint16 resist_diff = 0])
$mob->Spin()
$mob->StartEnrage()
$mob->Stun(int duration)
$mob->TempName(string name)
$mob->ThrowingAttack(mob* other)
$mob->TryMoveAlong(float distance, float angle, bool send)
$mob->TypesTempPet(uint32 type_id, [string name = nullptr], [uint32 duration = 0], [bool follow = 0], [mob* target = nullptr], [bool stick_targ = 0])
$mob->WearChange(uint8 material_slot, uint16 texture, [uint32 color = 0, uint32 hero_forge_model = 0])
$mob->WipeHateList()
```
{% endtab %}

{% tab title="Lua" %}
```lua
mob:AddNimbusEffect(int effect_id); -- void
mob:AddToHateList(Lua_Mob other); -- void
mob:AddToHateList(Lua_Mob other, int hate); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage, bool yell_for_help); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage, bool yell_for_help, bool frenzy); -- void
mob:AddToHateList(Lua_Mob other, int hate, int damage, bool yell_for_help, bool frenzy, bool buff_tic); -- void
mob:Attack(Lua_Mob other); -- bool
mob:Attack(Lua_Mob other, int hand); -- bool
mob:Attack(Lua_Mob other, int hand, bool from_riposte); -- bool
mob:Attack(Lua_Mob other, int hand, bool from_riposte, bool is_strikethrough); -- bool
mob:Attack(Lua_Mob other, int hand, bool from_riposte, bool is_strikethrough, bool is_from_spell); -- bool
mob:AttackAnimation(int Hand, Lua_ItemInst weapon); -- int
mob:BehindMob(); -- bool
mob:BehindMob(Lua_Mob other); -- bool
mob:BehindMob(Lua_Mob other, float x); -- bool
mob:BehindMob(Lua_Mob other, float x, float y); -- bool
mob:BuffCount(); -- uint32
mob:BuffFadeAll(); -- void
mob:BuffFadeByEffect(int effect_id); -- void
mob:BuffFadeByEffect(int effect_id, int skipslot); -- void
mob:BuffFadeBySlot(int slot); -- void
mob:BuffFadeBySlot(int slot, bool recalc_bonuses); -- void
mob:BuffFadeBySpellID(int spell_id); -- void
mob:CalculateDistance(double x, double y, double z); -- float
mob:CalculateHeadingToTarget(double in_x, double in_y); -- double
mob:CameraEffect(uint32 duration, uint32 intensity); -- void
mob:CameraEffect(uint32 duration, uint32 intensity, Lua_Client c); -- void
mob:CameraEffect(uint32 duration, uint32 intensity, Lua_Client c, bool global); -- void
mob:CanBuffStack(int spell_id, int caster_level); -- int
mob:CanBuffStack(int spell_id, int caster_level, bool fail_if_overwrite); -- int
mob:CanThisClassBlock(); -- bool
mob:CanThisClassDodge(); -- bool
mob:CanThisClassDoubleAttack(); -- bool
mob:CanThisClassDualWield(); -- bool
mob:CanThisClassParry(); -- bool
mob:CanThisClassRiposte(); -- bool
mob:CastSpell(int spell_id, int target_id); -- bool
mob:CastSpell(int spell_id, int target_id, int slot); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost, int item_slot); -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost, int item_slot, int timer,; -- bool
mob:CastSpell(int spell_id, int target_id, int slot, int cast_time, int mana_cost, int item_slot, int timer,; -- bool
mob:ChangeBeard(int in); -- void
mob:ChangeBeardColor(int in); -- void
mob:ChangeDrakkinDetails(int in); -- void
mob:ChangeDrakkinHeritage(int in); -- void
mob:ChangeDrakkinTattoo(int in); -- void
mob:ChangeEyeColor1(int in); -- void
mob:ChangeEyeColor2(int in); -- void
mob:ChangeGender(int in); -- void
mob:ChangeHairColor(int in); -- void
mob:ChangeHairStyle(int in); -- void
mob:ChangeHelmTexture(int in); -- void
mob:ChangeLuclinFace(int in); -- void
mob:ChangeRace(int in); -- void
mob:ChangeSize(double in_size); -- void
mob:ChangeSize(double in_size, bool no_restriction); -- void
mob:ChangeTexture(int in); -- void
mob:Charmed(); -- bool
mob:CheckAggro(Lua_Mob other); -- bool
mob:CheckAggroAmount(int spell_id); -- int
mob:CheckAggroAmount(int spell_id, bool is_proc); -- int
mob:CheckHealAggroAmount(int spell_id); -- int
mob:CheckHealAggroAmount(int spell_id, uint32 heal_possible); -- int
mob:CheckLoS(Lua_Mob other); -- bool
mob:CheckLoSToLoc(double x, double y, double z); -- bool
mob:CheckLoSToLoc(double x, double y, double z, double mob_size); -- bool
mob:CheckNumHitsRemaining(int type, int32 buff_slot, uint16 spell_id); -- void
mob:ClearSpecialAbilities(); -- void
mob:CombatRange(Lua_Mob other); -- bool
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill); -- void
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill, bool avoidable); -- void
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill, bool avoidable, int buffslot); -- void
mob:Damage(Lua_Mob from, int damage, int spell_id, int attack_skill, bool avoidable, int buffslot, bool buff_tic); -- void
mob:DelGlobal(const char *varname); -- void
mob:Depop(); -- void
mob:Depop(bool start_spawn_timer); -- void
mob:DivineAura(); -- bool
mob:DoAnim(int anim_num); -- void
mob:DoAnim(int anim_num, int type); -- void
mob:DoAnim(int anim_num, int type, bool ackreq); -- void
mob:DoAnim(int anim_num, int type, bool ackreq, int filter); -- void
mob:DoArcheryAttackDmg(Lua_Mob other); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo, int weapon_damage); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo, int weapon_damage, int chance_mod); -- void
mob:DoArcheryAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_ItemInst ammo, int weapon_damage, int chance_mod,; -- void
mob:DoKnockback(Lua_Mob caster, uint32 pushback, uint32 pushup); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill, int chance_mod); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill, int chance_mod, int focus); -- void
mob:DoMeleeSkillAttackDmg(Lua_Mob other, int weapon_damage, int skill, int chance_mod, int focus, bool can_riposte); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage, int min_damage); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage, int min_damage, int hate_override); -- void
mob:DoSpecialAttackDamage(Lua_Mob other, int skill, int max_damage, int min_damage, int hate_override, int reuse_time); -- void
mob:DoThrowingAttackDmg(Lua_Mob other); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item, int weapon_damage); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item, int weapon_damage, int chance_mod); -- void
mob:DoThrowingAttackDmg(Lua_Mob other, Lua_ItemInst range_weapon, Lua_Item item, int weapon_damage, int chance_mod,; -- void
mob:DoubleAggro(Lua_Mob other); -- void
mob:Emote(const char *message); -- void
mob:EntityVariableExists(const char *name); -- bool
mob:FaceTarget(Lua_Mob target); -- void
mob:FindBuff(int spell_id); -- bool
mob:FindBuffBySlot(int slot); -- uint16
mob:FindGroundZ(double x, double y); -- double
mob:FindGroundZ(double x, double y, double z); -- double
mob:FindType(int type); -- bool
mob:FindType(int type, bool offensive); -- bool
mob:FindType(int type, bool offensive, int threshold); -- bool
mob:GMMove(double x, double y, double z); -- void
mob:GMMove(double x, double y, double z, double heading); -- void
mob:GMMove(double x, double y, double z, double heading, bool send_update); -- void
mob:Gate(); -- void
mob:GetAA(int id); -- int
mob:GetAABonuses(); -- Lua_StatBonuses
mob:GetAAByAAID(int id); -- int
mob:GetAC(); -- int
mob:GetAGI(); -- int
mob:GetATK(); -- int
mob:GetAggroRange(); -- float
mob:GetAllowBeneficial(); -- bool
mob:GetAppearance(); -- uint32
mob:GetAssistRange(); -- float
mob:GetBaseGender(); -- int
mob:GetBaseRace(); -- int
mob:GetBaseSize(); -- float
mob:GetBeard(); -- int
mob:GetBeardColor(); -- int
mob:GetBodyType(); -- int
mob:GetBuffSlotFromType(int slot); -- int
mob:GetCHA(); -- int
mob:GetCR(); -- int
mob:GetCasterLevel(int spell_id); -- int
mob:GetClass(); -- int
mob:GetCorruption(); -- int
mob:GetDEX(); -- int
mob:GetDR(); -- int
mob:GetDamageAmount(Lua_Mob target); -- uint32
mob:GetDeity(); -- int
mob:GetDrakkinDetails(); -- int
mob:GetDrakkinHeritage(); -- int
mob:GetDrakkinTattoo(); -- int
mob:GetEyeColor1(); -- int
mob:GetEyeColor2(); -- int
mob:GetFR(); -- int
mob:GetFcDamageAmtIncoming(Lua_Mob caster, uint32 spell_id, bool use_skill, uint16 skill); -- int
mob:GetFlurryChance(); -- int
mob:GetGender(); -- int
mob:GetGlobal(const char *varname); -- std::string
mob:GetHP(); -- int
mob:GetHPRatio(); -- double
mob:GetHairColor(); -- int
mob:GetHairStyle(); -- int
mob:GetHandToHandDamage(); -- int
mob:GetHandToHandDelay(); -- int
mob:GetHaste(); -- int
mob:GetHateAmount(Lua_Mob target); -- uint32
mob:GetHateAmount(Lua_Mob target, bool is_damage); -- uint32
mob:GetHateDamageTop(Lua_Mob other); -- Lua_Mob
mob:GetHateList(); -- Lua_HateList
mob:GetHateRandom(); -- Lua_Mob
mob:GetHateTop(); -- Lua_Mob
mob:GetHeading(); -- double
mob:GetHelmTexture(); -- int
mob:GetHerosForgeModel(uint8 material_slot); -- uint32
mob:GetINT(); -- int
mob:GetInvul(); -- bool
mob:GetItemBonuses(); -- Lua_StatBonuses
mob:GetItemHPBonuses(); -- int
mob:GetItemStat(uint32 itemid, const char* identifier); -- int
mob:GetLevel(); -- int
mob:GetLevelCon(int my, int other); -- uint32
mob:GetLevelCon(int other); -- uint32
mob:GetLuclinFace(); -- int
mob:GetMR(); -- int
mob:GetMana(); -- int
mob:GetManaRatio(); -- double
mob:GetMaxAGI(); -- int
mob:GetMaxCHA(); -- int
mob:GetMaxDEX(); -- int
mob:GetMaxHP(); -- int
mob:GetMaxINT(); -- int
mob:GetMaxMana(); -- int
mob:GetMaxSTA(); -- int
mob:GetMaxSTR(); -- int
mob:GetMaxWIS(); -- int
mob:GetMeleeDamageMod_SE(uint16 skill); -- int16
mob:GetMeleeMinDamageMod_SE(uint16 skill); -- int16
mob:GetMeleeMitigation(); -- int32
mob:GetModSkillDmgTaken(int skill); -- int
mob:GetModVulnerability(int resist); -- int
mob:GetNPCTypeID(); -- int
mob:GetNimbusEffect1(); -- uint8
mob:GetNimbusEffect2(); -- uint8
mob:GetNimbusEffect3(); -- uint8
mob:GetOrigBodyType(); -- int
mob:GetOwner(); -- Lua_Mob
mob:GetPR(); -- int
mob:GetPet(); -- Lua_Mob
mob:GetPetOrder(); -- int
mob:GetPhR(); -- int
mob:GetRace(); -- int
mob:GetResist(int type); -- int
mob:GetReverseFactionCon(Lua_Mob other); -- int
mob:GetRunspeed(); -- double
mob:GetSTA(); -- int
mob:GetSTR(); -- int
mob:GetSize(); -- double
mob:GetSkill(int skill); -- int
mob:GetSkillDmgAmt(uint16 skill); -- int
mob:GetSkillDmgTaken(int skill); -- int
mob:GetSpecialAbility(int ability); -- int
mob:GetSpecialAbilityParam(int ability, int param); -- int
mob:GetSpecializeSkillValue(int spell_id); -- int
mob:GetSpellBonuses(); -- Lua_StatBonuses
mob:GetSpellHPBonuses(); -- int
mob:GetTarget(); -- Lua_Mob
mob:GetTexture(); -- int
mob:GetWIS(); -- int
mob:GetWalkspeed(); -- double
mob:GetWaypointH(); -- double
mob:GetWaypointID(); -- int
mob:GetWaypointPause(); -- double
mob:GetWaypointX(); -- double
mob:GetWaypointY(); -- double
mob:GetWaypointZ(); -- double
mob:GetWeaponDamage(Lua_Mob against, Lua_ItemInst weapon); -- int
mob:GetWeaponDamageBonus(Lua_Item weapon, bool offhand); -- int
mob:GetX(); -- double
mob:GetY(); -- double
mob:GetZ(); -- double
mob:GotoBind(); -- void
mob:HalveAggro(Lua_Mob other); -- void
mob:HasNPCSpecialAtk(const char *parse); -- bool
mob:HasOwner(); -- bool
mob:HasPet(); -- bool
mob:HasProcs(); -- bool
mob:HasShieldEquiped(); -- bool
mob:HasTwoHandBluntEquiped(); -- bool
mob:HasTwoHanderEquipped(); -- bool
mob:Heal(); -- void
mob:HealDamage(uint32 amount); -- void
mob:HealDamage(uint32 amount, Lua_Mob other); -- void
mob:InterruptSpell(); -- void
mob:InterruptSpell(int spell_id); -- void
mob:IsAIControlled(); -- bool
mob:IsAmnesiad(); -- bool
mob:IsAttackAllowed(Lua_Mob target, bool isSpellAttack); -- bool
mob:IsBeneficialAllowed(Lua_Mob target); -- bool
mob:IsBerserk(); -- bool
mob:IsBlind(); -- bool
mob:IsCasting(); -- bool
mob:IsEliteMaterialItem(uint8 material_slot); -- uint32
mob:IsEngaged(); -- bool
mob:IsEnraged(); -- bool
mob:IsFeared(); -- bool
mob:IsImmuneToSpell(int spell_id, Lua_Mob caster); -- bool
mob:IsInvisible(); -- bool
mob:IsInvisible(Lua_Mob other); -- bool
mob:IsMeleeDisabled(); -- bool
mob:IsMezzed(); -- bool
mob:IsMoving(); -- bool
mob:IsPet(); -- bool
mob:IsRoamer(); -- bool
mob:IsRooted(); -- bool
mob:IsRunning(); -- bool
mob:IsSilenced(); -- bool
mob:IsStunned(); -- bool
mob:IsTargetable(); -- bool
mob:IsTargeted(); -- bool
mob:IsWarriorClass(); -- bool
mob:Kill(); -- void
mob:Mesmerize(); -- void
mob:Message(int type, const char *message); -- void
mob:MessageString(int type, int string_id, uint32 distance); -- void
mob:ModSkillDmgTaken(int skill, int value); -- void
mob:ModVulnerability(int resist, int value); -- void
mob:NPCSpecialAttacks(const char *parse, int perm); -- void
mob:NPCSpecialAttacks(const char *parse, int perm, bool reset); -- void
mob:NPCSpecialAttacks(const char *parse, int perm, bool reset, bool remove); -- void
mob:NavigateTo(double x, double y, double z); -- void
mob:ProcessSpecialAbilities(std::string str); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed, double angle); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed, double angle, double tilt); -- void
mob:ProjectileAnimation(Lua_Mob to, int item_id, bool is_arrow, double speed, double angle, double tilt, double arc); -- void
mob:QuestSay(Lua_Client client, const char *message); -- void
mob:RandomizeFeatures(bool send_illusion, bool save_variables); -- void
mob:RangedAttack(Lua_Mob other); -- void
mob:RemoveNimbusEffect(int effect_id); -- void
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster); -- double
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster, bool use_resist_override); -- double
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster, bool use_resist_override, int resist_override); -- double
mob:ResistSpell(int resist_type, int spell_id, Lua_Mob caster, bool use_resist_override, int resist_override,; -- double
mob:RunTo(double x, double y, double z); -- void
mob:Say(const char *message); -- void
mob:Say(const char* message, int language); -- void
mob:SeeHide(); -- bool
mob:SeeImprovedHide(); -- bool
mob:SeeInvisible(); -- uint8
mob:SeeInvisibleUndead(); -- bool
mob:SendAppearanceEffect(uint32 parm1, uint32 parm2, uint32 parm3, uint32 parm4, uint32 parm5); -- void
mob:SendAppearanceEffect(uint32 parm1, uint32 parm2, uint32 parm3, uint32 parm4, uint32 parm5, Lua_Client specific_target); -- void
mob:SendBeginCast(int spell_id, int cast_time); -- void
mob:SendSpellEffect(uint32 effect_id, uint32 duration, uint32 finish_delay, bool zone_wide, uint32 unk020); -- void
mob:SendSpellEffect(uint32 effect_id, uint32 duration, uint32 finish_delay, bool zone_wide, uint32 unk020, bool perm_effect); -- void
mob:SendSpellEffect(uint32 effect_id, uint32 duration, uint32 finish_delay, bool zone_wide, uint32 unk020, bool perm_effect,; -- void
mob:SendTo(double x, double y, double z); -- void
mob:SendToFixZ(double x, double y, double z); -- void
mob:SendWearChange(int material_slot); -- void
mob:SetAA(int rank_id, int new_value); -- bool
mob:SetAA(int rank_id, int new_value, int charges); -- bool
mob:SetAllowBeneficial(bool value); -- void
mob:SetAppearance(int app); -- void
mob:SetAppearance(int app, bool ignore_self); -- void
mob:SetBodyType(int new_body, bool overwrite_orig); -- void
mob:SetCurrentWP(int wp); -- void
mob:SetDestructibleObject(bool set); -- void
mob:SetDisableMelee(bool disable); -- void
mob:SetEntityVariable(const char *name, const char *value); -- void
mob:SetExtraHaste(int haste); -- void
mob:SetFlurryChance(int value); -- void
mob:SetFlyMode(int in); -- void
mob:SetGender(int in); -- void
mob:SetGlobal(const char *varname, const char *newvalue, int options, const char *duration); -- void
mob:SetGlobal(const char *varname, const char *newvalue, int options, const char *duration, Lua_Mob other); -- void
mob:SetHP(int hp); -- void
mob:SetHate(Lua_Mob other); -- void
mob:SetHate(Lua_Mob other, int hate); -- void
mob:SetHate(Lua_Mob other, int hate, int damage); -- void
mob:SetHeading(double in); -- void
mob:SetInvisible(int state); -- void
mob:SetInvul(bool value); -- void
mob:SetLevel(int level); -- void
mob:SetLevel(int level, bool command); -- void
mob:SetMana(int mana); -- int
mob:SetOOCRegen(int regen); -- void
mob:SetPetOrder(int order); -- void
mob:SetPseudoRoot(bool in); -- void
mob:SetRace(int in); -- void
mob:SetRunning(bool running); -- void
mob:SetSlotTint(int material_slot, int red_tint, int green_tint, int blue_tint); -- void
mob:SetSpecialAbility(int ability, int level); -- void
mob:SetSpecialAbilityParam(int ability, int param, int value); -- void
mob:SetTarget(Lua_Mob t); -- void
mob:SetTargetable(bool on); -- void
mob:SetTexture(int in); -- void
mob:Shout(const char *message); -- void
mob:Shout(const char* message, int language); -- void
mob:Signal(uint32 id); -- void
mob:SpellEffect(Lua_Mob caster, int spell_id, double partial); -- void
mob:SpellFinished(int spell_id, Lua_Mob target); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used, uint32 inventory_slot); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used, uint32 inventory_slot, int resist_adjust); -- bool
mob:SpellFinished(int spell_id, Lua_Mob target, int slot, int mana_used, uint32 inventory_slot, int resist_adjust, bool proc); -- bool
mob:Spin(); -- void
mob:StopNavigation(); -- void
mob:Stun(int duration); -- void
mob:TarGlobal(const char *varname, const char *value, const char *duration, int npc_id, int char_id, int zone_id); -- void
mob:TempName(); -- void
mob:TempName(const char *newname); -- void
mob:ThrowingAttack(Lua_Mob other); -- void
mob:TryFinishingBlow(Lua_Mob defender, int &damage); -- bool
mob:TryMoveAlong(float distance, float angle); -- void
mob:TryMoveAlong(float distance, float angle, bool send); -- void
mob:UnStun(); -- void
mob:WalkTo(double x, double y, double z); -- void
mob:WearChange(int material_slot, int texture, uint32 color); -- void
mob:WipeHateList(); -- void
```
{% endtab %}
{% endtabs %}

