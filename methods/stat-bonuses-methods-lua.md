# Stat Bonuses Methods \(Lua\)

{% tabs %}
{% tab title="Lua" %}
```lua
statbonuses:GetAC() const; -- int32
statbonuses:GetAGI() const; -- int32
statbonuses:GetAGICapMod() const; -- int32
statbonuses:GetAStacker(int idx) const; -- int32
statbonuses:GetATK() const; -- int32
statbonuses:GetAbsorbMagicAtt(int idx) const; -- uint32
statbonuses:GetAccuracy(int idx) const; -- int32
statbonuses:GetAggroRange() const; -- float
statbonuses:GetAlterNPCLevel() const; -- int32
statbonuses:GetAmbidexterity() const; -- int32
statbonuses:GetAmplification() const; -- uint32
statbonuses:GetAntiGate() const; -- bool
statbonuses:GetArcheryDamageModifier() const; -- uint32
statbonuses:GetAssassinate(int idx) const; -- uint32
statbonuses:GetAssassinateLevel(int idx) const; -- uint8
statbonuses:GetAssistRange() const; -- float
statbonuses:GetAvoidMeleeChance() const; -- int32
statbonuses:GetAvoidMeleeChanceEffect() const; -- int32
statbonuses:GetBStacker(int idx) const; -- int32
statbonuses:GetBaseMovementSpeed() const; -- int8
statbonuses:GetBerserkSPA() const; -- bool
statbonuses:GetBindWound() const; -- int32
statbonuses:GetBlockBehind() const; -- int32
statbonuses:GetBlockNextSpell() const; -- bool
statbonuses:GetBuffSlotIncrease() const; -- uint8
statbonuses:GetCHA() const; -- int32
statbonuses:GetCHACapMod() const; -- int32
statbonuses:GetCR() const; -- int32
statbonuses:GetCRCapMod() const; -- int32
statbonuses:GetCStacker(int idx) const; -- int32
statbonuses:GetChannelChanceItems() const; -- int32
statbonuses:GetChannelChanceSpells() const; -- int32
statbonuses:GetCharmBreakChance() const; -- int32
statbonuses:GetClairvoyance() const; -- int32
statbonuses:GetCombatStability() const; -- int32
statbonuses:GetConsumeProjectile() const; -- uint8
statbonuses:GetCorrup() const; -- int32
statbonuses:GetCorrupCapMod() const; -- int32
statbonuses:GetCrippBlowChance() const; -- int32
statbonuses:GetCritDmgMod(int idx) const; -- int32
statbonuses:GetCriticalDoTChance() const; -- int32
statbonuses:GetCriticalDotDecay() const; -- bool
statbonuses:GetCriticalHealChance() const; -- int32
statbonuses:GetCriticalHealDecay() const; -- bool
statbonuses:GetCriticalHealOverTime() const; -- int32
statbonuses:GetCriticalHitChance(int idx) const; -- int32
statbonuses:GetCriticalMend() const; -- int8
statbonuses:GetCriticalRegenDecay() const; -- bool
statbonuses:GetCriticalSpellChance() const; -- int32
statbonuses:GetDEX() const; -- int32
statbonuses:GetDEXCapMod() const; -- int32
statbonuses:GetDR() const; -- int32
statbonuses:GetDRCapMod() const; -- int32
statbonuses:GetDSMitigation() const; -- int32
statbonuses:GetDSMitigationOffHand() const; -- int32
statbonuses:GetDStacker(int idx) const; -- int32
statbonuses:GetDamageModifier(int idx) const; -- int32
statbonuses:GetDamageModifier2(int idx) const; -- int32
statbonuses:GetDamageShield() const; -- int
statbonuses:GetDamageShieldSpellID() const; -- uint16
statbonuses:GetDamageShieldType() const; -- int
statbonuses:GetDeathSave(int idx) const; -- uint32
statbonuses:GetDelayDeath() const; -- uint32
statbonuses:GetDistanceRemoval() const; -- bool
statbonuses:GetDivineAura() const; -- bool
statbonuses:GetDivineSaveChance(int idx) const; -- int32
statbonuses:GetDoTShielding() const; -- int32
statbonuses:GetDodgeChance() const; -- int32
statbonuses:GetDotCritDmgIncrease() const; -- int32
statbonuses:GetDoubleAttackChance() const; -- int32
statbonuses:GetDoubleRangedAttack() const; -- int32
statbonuses:GetDoubleRiposte() const; -- int32
statbonuses:GetDoubleSpecialAttack() const; -- int32
statbonuses:GetDualWieldChance() const; -- int32
statbonuses:GetEndPercCap(int idx) const; -- int
statbonuses:GetEndurance() const; -- int32
statbonuses:GetEnduranceReduction() const; -- int32
statbonuses:GetEnduranceRegen() const; -- int32
statbonuses:GetExtraAttackChance() const; -- int32
statbonuses:GetFR() const; -- int32
statbonuses:GetFRCapMod() const; -- int32
statbonuses:GetFactionModPct() const; -- int32
statbonuses:GetFearless() const; -- bool
statbonuses:GetFeignedCastOnChance() const; -- int16
statbonuses:GetFinishingBlow(int idx) const; -- int32
statbonuses:GetFinishingBlowLvl(int idx) const; -- uint32
statbonuses:GetFlurryChance() const; -- int32
statbonuses:GetFocusEffects(int idx) const; -- uint8
statbonuses:GetFocusEffectsWorn(int idx) const; -- int16
statbonuses:GetForageAdditionalItems() const; -- uint8
statbonuses:GetFrenziedDevastation() const; -- int32
statbonuses:GetFrontalBackstabChance() const; -- uint8
statbonuses:GetFrontalBackstabMinDmg() const; -- bool
statbonuses:GetFrontalStunResist() const; -- uint8
statbonuses:GetGiveDoubleAttack() const; -- uint32
statbonuses:GetGiveDoubleRiposte(int idx) const; -- int32
statbonuses:GetGivePetGroupTarget() const; -- bool
statbonuses:GetGravityEffect() const; -- int32
statbonuses:GetHP() const; -- int32
statbonuses:GetHPPercCap(int idx) const; -- int
statbonuses:GetHPRegen() const; -- int32
statbonuses:GetHPToManaConvert() const; -- uint32
statbonuses:GetHSLevel(int idx) const; -- uint8
statbonuses:GetHeadShot(int idx) const; -- uint32
statbonuses:GetHealAmt() const; -- int32
statbonuses:GetHealRate() const; -- int32
statbonuses:GetHeroicAGI() const; -- int32
statbonuses:GetHeroicCHA() const; -- int32
statbonuses:GetHeroicCR() const; -- int32
statbonuses:GetHeroicCorrup() const; -- int32
statbonuses:GetHeroicDEX() const; -- int32
statbonuses:GetHeroicDR() const; -- int32
statbonuses:GetHeroicFR() const; -- int32
statbonuses:GetHeroicINT() const; -- int32
statbonuses:GetHeroicMR() const; -- int32
statbonuses:GetHeroicPR() const; -- int32
statbonuses:GetHeroicSTA() const; -- int32
statbonuses:GetHeroicSTR() const; -- int32
statbonuses:GetHeroicWIS() const; -- int32
statbonuses:GetHitChance() const; -- int32
statbonuses:GetHitChanceEffect(int idx) const; -- int32
statbonuses:GetHundredHands() const; -- int32
statbonuses:GetINT() const; -- int32
statbonuses:GetINTCapMod() const; -- int32
statbonuses:GetIllusionPersistence() const; -- bool
statbonuses:GetImmuneToFlee() const; -- bool
statbonuses:GetImprovedReclaimEnergy() const; -- int32
statbonuses:GetImprovedTaunt(int idx) const; -- int32
statbonuses:GetIncreaseBlockChance() const; -- int32
statbonuses:GetIncreaseChanceMemwipe() const; -- int8
statbonuses:GetIncreaseRunSpeedCap() const; -- uint8
statbonuses:GetIsBlind() const; -- bool
statbonuses:GetIsFeared() const; -- bool
statbonuses:GetItemATKCap() const; -- int32
statbonuses:GetItemHPRegenCap() const; -- int32
statbonuses:GetItemManaRegenCap() const; -- uint32
statbonuses:GetLimitToSkill(int idx) const; -- bool
statbonuses:GetMR() const; -- int32
statbonuses:GetMRCapMod() const; -- int32
statbonuses:GetMagicWeapon() const; -- bool
statbonuses:GetMana() const; -- int32
statbonuses:GetManaAbsorbPercentDamage(int idx) const; -- uint32
statbonuses:GetManaPercCap(int idx) const; -- int
statbonuses:GetManaRegen() const; -- int32
statbonuses:GetMasteryofPast() const; -- uint8
statbonuses:GetMaxBindWound() const; -- int32
statbonuses:GetMaxHP() const; -- int32
statbonuses:GetMaxHPChange() const; -- int32
statbonuses:GetMeleeLifetap() const; -- int32
statbonuses:GetMeleeMitigation() const; -- int32
statbonuses:GetMeleeMitigationEffect() const; -- int32
statbonuses:GetMeleeRune(int idx) const; -- uint32
statbonuses:GetMeleeSkillCheck() const; -- int32
statbonuses:GetMeleeSkillCheckSkill() const; -- uint8
statbonuses:GetMeleeThresholdGuard(int idx) const; -- uint32
statbonuses:GetMetabolism() const; -- int32
statbonuses:GetMinDamageModifier(int idx) const; -- int32
statbonuses:GetMitigateDotRune(int idx) const; -- uint32
statbonuses:GetMitigateMeleeRune(int idx) const; -- uint32
statbonuses:GetMitigateSpellRune(int idx) const; -- uint32
statbonuses:GetNegateAttacks(int idx) const; -- uint32
statbonuses:GetNegateEffects() const; -- bool
statbonuses:GetNegateIfCombat() const; -- bool
statbonuses:GetNoBreakAESneak() const; -- int16
statbonuses:GetOffhandRiposteFail() const; -- int32
statbonuses:GetPC_Pet_Flurry() const; -- uint32
statbonuses:GetPC_Pet_Rampage(int idx) const; -- uint32
statbonuses:GetPR() const; -- int32
statbonuses:GetPRCapMod() const; -- int32
statbonuses:GetPackrat() const; -- int8
statbonuses:GetParryChance() const; -- int32
statbonuses:GetPersistantCasting() const; -- uint32
statbonuses:GetPetAvoidance() const; -- int32
statbonuses:GetPetCriticalHit() const; -- int32
statbonuses:GetPetFlurry() const; -- int32
statbonuses:GetPetMaxHP() const; -- int32
statbonuses:GetPetMeleeMitigation() const; -- int32
statbonuses:GetProcChance() const; -- int32
statbonuses:GetProcChanceSPA() const; -- int32
statbonuses:GetRaiseSkillCap(int idx) const; -- uint32
statbonuses:GetReduceFallDamage() const; -- uint16
statbonuses:GetReduceTradeskillFail(int idx) const; -- int32
statbonuses:GetResistFearChance() const; -- int32
statbonuses:GetResistSpellChance() const; -- int32
statbonuses:GetReverseDamageShield() const; -- int
statbonuses:GetReverseDamageShieldSpellID() const; -- uint16
statbonuses:GetReverseDamageShieldType() const; -- int
statbonuses:GetRiposteChance() const; -- int32
statbonuses:GetRoot(int idx) const; -- int8
statbonuses:GetRootBreakChance() const; -- int32
statbonuses:GetSEResist(int idx) const; -- int32
statbonuses:GetSTA() const; -- int32
statbonuses:GetSTACapMod() const; -- int32
statbonuses:GetSTR() const; -- int32
statbonuses:GetSTRCapMod() const; -- int32
statbonuses:GetSalvageChance() const; -- uint8
statbonuses:GetSanctuary() const; -- bool
statbonuses:GetScreech() const; -- int8
statbonuses:GetSecondaryDmgInc() const; -- bool
statbonuses:GetSeeInvis() const; -- uint8
statbonuses:GetShieldBlock() const; -- int32
statbonuses:GetShieldEquipDmgMod() const; -- int32
statbonuses:GetShroudofStealth() const; -- bool
statbonuses:GetSkillAttackProc(int idx) const; -- int32
statbonuses:GetSkillDamageAmount(int idx) const; -- int32
statbonuses:GetSkillDamageAmount2(int idx) const; -- int32
statbonuses:GetSkillDmgTaken(int idx) const; -- int16
statbonuses:GetSkillProc(int idx) const; -- uint32
statbonuses:GetSkillProcSuccess(int idx) const; -- uint32
statbonuses:GetSkillReuseTime(int idx) const; -- int32
statbonuses:GetSlayUndead(int idx) const; -- int32
statbonuses:GetSongRange() const; -- int32
statbonuses:GetSpellCritDmgIncNoStack() const; -- int32
statbonuses:GetSpellCritDmgIncrease() const; -- int32
statbonuses:GetSpellDamageShield() const; -- int
statbonuses:GetSpellDmg() const; -- int32
statbonuses:GetSpellOnDeath(int idx) const; -- uint32
statbonuses:GetSpellOnKill(int idx) const; -- uint32
statbonuses:GetSpellProcChance() const; -- int32
statbonuses:GetSpellShield() const; -- int
statbonuses:GetSpellThresholdGuard(int idx) const; -- uint32
statbonuses:GetSpellTriggers(int idx) const; -- uint32
statbonuses:GetStrikeThrough() const; -- int32
statbonuses:GetStunBashChance() const; -- int8
statbonuses:GetStunResist() const; -- int32
statbonuses:GetTradeSkillMastery() const; -- uint8
statbonuses:GetTriggerMeleeThreshold() const; -- bool
statbonuses:GetTriggerOnValueAmount() const; -- bool
statbonuses:GetTriggerSpellThreshold() const; -- bool
statbonuses:GetTripleAttackChance() const; -- int32
statbonuses:GetTripleBackstab() const; -- uint8
statbonuses:GetTwoHandBluntBlock() const; -- int32
statbonuses:GetUnfailingDivinity() const; -- int32
statbonuses:GetVampirism() const; -- int32
statbonuses:GetVoiceGraft() const; -- uint32
statbonuses:GetWIS() const; -- int32
statbonuses:GetWISCapMod() const; -- int32
statbonuses:GetXPRateMod() const; -- int
statbonuses:GetbrassMod() const; -- uint32
statbonuses:Geteffective_casting_level() const; -- int
statbonuses:Getextra_xtargets() const; -- uint16
statbonuses:Gethaste() const; -- int32
statbonuses:Gethastetype2() const; -- int32
statbonuses:Gethastetype3() const; -- int32
statbonuses:Gethatemod() const; -- int8
statbonuses:Getinhibitmelee() const; -- int32
statbonuses:Getmovementspeed() const; -- int
statbonuses:GetpercussionMod() const; -- uint32
statbonuses:Getreflect_chance() const; -- int
statbonuses:GetsingingMod() const; -- uint32
statbonuses:Getskillmod(int idx) const; -- int32
statbonuses:Getskillmodmax(int idx) const; -- int32
statbonuses:GetsongModCap() const; -- uint32
statbonuses:GetstringedMod() const; -- uint32
statbonuses:GetwindMod() const; -- uint32
```
{% endtab %}
{% endtabs %}

