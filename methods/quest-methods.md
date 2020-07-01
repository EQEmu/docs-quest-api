# Quest Methods

{% tabs %}
{% tab title="Perl" %}
```perl
quest::AssignGroupToInstance(uint16 instance_id)
quest::AssignRaidToInstance(uint16 instance_id)
quest::AssignToInstance(uint16 instance_id)
quest::AssignToInstanceByCharID(uint16 instance_id, uint32 char_id)
quest::CheckInstanceByCharID(uint16 instance_id, uint32 char_id)
quest::ChooseRandom(option1, option2, option3, option4, option5...[no limit])
quest::CreateInstance(string zone_name, uint16 version, uint32 duration)
quest::DestroyInstance(int id)
quest::FlagInstanceByGroupLeader(uint32 zone, uint16 version)
quest::FlagInstanceByRaidLeader(uint32 zone, uint16 version)
quest::FlyMode(uint8 mode [0-5])
quest::GetCharactersInInstance(uint16 instance_id)
quest::GetInstanceID(string zone_name, uint16 version)
quest::GetInstanceIDByCharID(string zone_name, uint16 version, uint32 char_id)
quest::GetInstanceTimer()
quest::GetInstanceTimerByID(uint16 instance_id)
quest::GetSpellResistType(uint32 spell_id)
quest::GetSpellTargetType(uint32 spell_id)
quest::GetTimeSeconds()
quest::GetZoneID(string zone)
quest::GetZoneLongName(string zone)
quest::IsBeneficialSpell(uint32 spell_id)
quest::IsEffectInSpell(uint32 spell_id, uint32 effect_id)
quest::IsRunning()
quest::LearnRecipe(int recipe_id)
quest::MerchantCountItem(uint32 npc_id, uint32 item_id)
quest::MerchantSetItem(uint32 npc_id, uint32 item_id, [uint32 quantity])
quest::ModifyNPCStat(string key, string value)
quest::MovePCInstance(int zone_id, int instance_id, float X, float Y, float Z, [float heading])
quest::RemoveAllFromInstance(uint16 instance_id)
quest::RemoveFromInstance(uint16 instance_id)
quest::RemoveFromInstanceByCharID(uint16 instance_id, uint32 char_id)
quest::SendMail(stirng to, string from, string subject, string message)
quest::SetRunning(bool is_running)
quest::UpdateInstanceTimer(int16 instance_id, uint32 duration)
quest::UpdateSpawnTimer(uint32 spawn2_id, uint32 updated_time_till_repop)
quest::UpdateZoneHeader(string key, string value)
quest::activespeakactivity(int task_id)
quest::activespeaktask()
quest::activetasksinset(int task_set)
quest::addldonloss(int losses, int theme_id)
quest::addldonpoints(int points, int theme_id)
quest::addldonwin(int wins, int theme_id)
quest::addloot(uint32 item_id, uint16 charges = 0, [bool equip_item = true])
quest::addskill(int skill_id, int value)
quest::assigntask(int task_id, [bool enforce_level_requirement = false])
quest::attack(string client_name)
quest::attacknpc(int npc_entity_id)
quest::attacknpctype(int npc_type_id)
quest::buryplayercorpse(int character_id)
quest::castspell(int spell_id, int target_id)
quest::changedeity(int deity_id)
quest::checktitle(int title_set_id)
quest::clear_npctype_cache(int npc_type_id)
quest::clear_proximity()
quest::clear_zone_flag(uint32 zone_id)
quest::clearspawntimers()
quest::collectitems(int item_id, [bool remove_item = true])
quest::completedtasksinset(int task_set)
quest::countitem(uint32 item_id)
quest::createBot(string first_name, string last_name, int level, int race_id, int class_id, int gender_id)
quest::createdoor(string model_name, float X, float Y, float Z, float heading, [int object_type = 58], [int size = 100])
quest::creategroundobject(int item_id, float X, float Y, float Z, float heading, [uint32 decay_time-ms = 300000])
quest::creategroundobjectfrommodel(string model_name, float X, float Y, float Z, float heading, [int object_type], [uint32 decay_time-ms = 300000])
quest::createguild(string guild_name, string leader_name)
quest::crosszoneassigntaskbycharid(int character_id, uint32 task_id, [bool enforce_level_requirement = false])
quest::crosszoneassigntaskbygroupid(int group_id, uint32 task_id, [bool enforce_level_requirement = false])
quest::crosszoneassigntaskbyraidid(int raid_id, uint32 task_id, [bool enforce_level_requirement = false])
quest::crosszoneassigntaskbyguildid(int guild_id, uint32 task_id, [bool enforce_level_requirement = false])
quest::crosszonemessageplayerbyname(int channel_id, string name, string message)
quest::crosszonemessageplayerbygroupid(int type, int group_id, string message)
quest::crosszonemessageplayerbyraidid(int type, int raid_id, string message)
quest::crosszonemessageplayerbyguildid(int type, int guild_id, string message)
quest::crosszonemoveplayerbycharid(int character_id, const char *zone_short_name)
quest::crosszonemoveplayerbygroupid(int group_id, const char *zone_short_name)
quest::crosszonemoveplayerbyraidid(int raid_id, const char *zone_short_name)
quest::crosszonemoveplayerbyguildid(int guild_id, const char *zone_short_name)
quest::crosszonesetentityvariablebyclientname(string client_name, string key, string value)
quest::crosszonesetentityvariablebygroupid(int group_id, ing client_name, string key, string value)
quest::crosszonesetentityvariablebyraidid(int raid_id, string key, string value)
quest::crosszonesetentityvariablebyguildid(int guild_id, string key, string value)
quest::crosszonesetentityvariablebynpctypeid(int npc_type_id, string key, string value)
quest::crosszonesignalclientbycharid(int character_id, int value)
quest::crosszonesignalclientbygroupid(int group_id, int value)
quest::crosszonesignalclientbyraidid(int raid_id, int value)
quest::crosszonesignalclientbyguildid(int guild_id, int value)
quest::crosszonesignalnpcbynpctypeid(uint32 npc_type_id, uint32 value)
quest::debug(string message, [uint8 debug_level = 1 [1-3]])
quest::delete_data(string bucket_key)
quest::delglobal(string key)
quest::depop(int npc_type_id = 0)
quest::depop_withtimer(int npc_type_id = 0)
quest::depopall(int npc_type_id = 0)
quest::depopzone([bool start_spawn_status = false])
quest::ding()
quest::disable_proximity_say()
quest::disable_spawn2(int spawn2_id)
quest::disablerecipe(int recipe_id)
quest::disabletask(int task_id, 2, 3, [up to 10])
quest::doanim(int animation_id)
quest::echo(int emote_color_id, string message)
quest::emote(string message)
quest::enable_proximity_say()
quest::enable_spawn2(int spawn2_id)
quest::enabledtaskcount(int task_set)
quest::enablerecipe(int recipe_id)
quest::enabletask(int task_id, 2, 3, [up to 10])
quest::enabletitle(int title_set_id)
quest::exp(int amount)
quest::faction(int faction_id, int value, [int temp = 0])
quest::factionvalue()
quest::failtask(int task_id)
quest::firsttaskinset(int task_set)
quest::follow(int entity_id, [int distance = 10])
quest::forcedoorclose(int door_id, [bool alt_mode = 0])
quest::forcedooropen(int door_id, [int alt_mode=0])
quest::getcharnamebyid(uint32 char_id)
quest::getcharidbyname(string name)
quest::getclassname(uint8 class_id, [uint8 level = 0])
quest::getcurrencyid(uint32 item_id)
quest::getcurrencyitemid(int currency_id)
quest::get_data(string bucket_key)
quest::get_data_expires(string bucket_key)
quest::get_rule(string rule_name)
quest::get_spawn_condition(string zone_short, [int instance_id], int condition_id)
quest::getguildnamebyid(uint32 guild_id)
quest::getinventoryslotid(string identifier)
quest::getitemname(uint32 item_id)
quest::getlevel(int type)
quest::getnpcnamebyid(uint32 npc_id)
quest::getplayerburiedcorpsecount(int character_id)
quest::getplayercorpsecount(uint32 char_id)
quest::getplayercorpsecountbyzoneid(uint32 char_id, uint32 zone_id)
quest::getracename(uint16 race_id)
quest::getskillname(int skill_id)
quest::getspellname(uint32 spell_id)
quest::gettaskactivitydonecount(int task_id, int activity_id)
quest::gettaskname(uint32 task_id)
quest::givecash(int copper, int silver, int gold, int platinum)
quest::gmmove(float X, float Y, float Z)
quest::gmsay(string message, [int color_id], [bool send_to_world = 0])
quest::has_zone_flag(uint32 zone_id)
quest::incstat(int stat_id, int value)
quest::isdisctome(int item_id)
quest::isdooropen(int door_id)
quest::istaskappropriate(int task_id)
quest::istaskactive(int task_id)
quest::istaskactivityactive(int task_id, int activity_id)
quest::istaskcompleted(int task_id)
quest::istaskenabled(int task_id)
quest::itemlink(int item_id)
quest::lasttaskinset(int task_set)
quest::level(int new_level)
quest::me(string message)
quest::movegrp(int zone_id, float X, float Y, float Z)
quest::movepc(int zone_id, float X, float Y, float Z [float heading])
quest::moveto(float X, float Y, float Z, [float heading], [bool save_guard_location])
quest::nexttaskinset(int task_set, int task_id)
quest::npcfeature(string feature [race|gender|texture|helm|haircolor|beardcolor|eyecolor1|eyecolor2|hair|face|beard|heritage|tatoo|details|size], int value)
quest::npcgender(int gender_id)
quest::npcrace(int race_id)
quest::npcsize(int size)
quest::npctexture(int texture_id)
quest::pause(int duration-ms)
quest::permaclass(int class_id)
quest::permagender(int gender_id)
quest::permarace(int race_id)
quest::playerfeature(string feature [race|gender|texture|helm|haircolor|beardcolor|eyecolor1|eyecolor2|hair|face|beard|heritage|tatoo|details|size], int setting)
quest::playergender(int gender_id)
quest::playerrace(int race_id)
quest::playersize(int newsize)
quest::playertexture(int texture_id)
quest::popup(string window_title, string message, int popup_id, int buttons, int duration)
quest::pvp(string mode [on|off])
quest::qs_player_event(int character_id, string message)
quest::qs_send_query(string query)
quest::rain(int weather)
quest::rebind(int zone_id, float X, float Y, float Z)
quest::removetitle(int title_set_id)
quest::repopzone()
quest::resettaskactivity(int task_id, int activity_id)
quest::respawn(int npc_type_id, int grid_id)
quest::resume()
quest::safemove()
quest::save()
quest::say(string message, [int language_id], [int message_type], [int speak_mode], [int journal_mode])
quest::saylink(string message, [bool silent = false], [link_name = message])
quest::scribespells(int max_level, [int min_level = 1])
quest::selfcast(int spell_id)
quest::set_data(string key, string value, [string expires_at = 0])
quest::set_proximity(float min_x, float max_x, float min_y, float max_y, [float min_z], [float max_z], [say])
quest::set_rule(string rule_name, string rule_value)
quest::set_zone_flag(uint32 zone_id)
quest::setallskill(int value)
quest::setanim(int npc_type_id, int appearance_number[0-4])
quest::setglobal(stirng key, string value, int options, string duration)
quest::setguild(int guild_id, int guild_rank_id)
quest::sethp(int mob_health_percentage [0-100])
quest::setlanguage(int skill_id, int value)
quest::setnexthpevent(int at_mob_percentage)
quest::setnextinchpevent(int at_mob_percentage)
quest::setskill(int skill_id, int value)
quest::setsky(uint8 sky)
quest::setstat(stat_id, int_value)
quest::settarget(string target_enum ['npc_type', 'entity'], int target_id)
quest::settime(int new_hour, int new_min, [bool update_world = true])
quest::settimer(string timer_name, int seconds)
quest::settimerMS(string timer_name, int milliseconds)
quest::sfollow()
quest::shout(string message)
quest::shout2(string message)
quest::showgrid(int grid_id)
quest::signal(int npc_id, [int wait_ms])
quest::signalwith(int npc_id, int signal_id, [int wait_ms])
quest::snow(int weather)
quest::spawn(int npc_type_id, int grid_id, int int_unused, float X, float Y, float Z)
quest::spawn2(int npc_type_id, int grid_id, int int_unused, float X, float Y, float Z, float heading)
quest::spawn_condition(string zone_short, [int instance_id], uint16 condition_id, int16 value)
quest::spawn_from_spawn2(int spawn2_id)
quest::start(int waypoint)
quest::stop()
quest::stopalltimers()
quest::stoptimer(string timer_name)
quest::summonallplayercorpses(int char_id, float dest_x, float dest_y, float dest_z, float dest_heading)
quest::summonburiedplayercorpse(uint32 char_id, float dest_x, float dest_y, float dest_z, float dest_heading)
quest::summonitem(int item_id, [int charges])
quest::surname(string name)
quest::targlobal(stirng key, string value, string duration, int npc_id, int chararacter_id, int zone_id)
quest::task_setselector(int task_set_id)
quest::taskexplorearea(int explore_id)
quest::taskselector(int task_id, 2, 3, 4, 5 [up to 40])
quest::tasktimeleft(int task_id)
quest::toggle_spawn_event(uint32 event_id, [bool is_enabled = false], [bool is_strict = false], [bool reset_base = false])
quest::toggledoorstate(int door_id)
quest::traindisc(int tome_item_id)
quest::traindiscs(int max_level, [int min_level = 1])
quest::unique_spawn(int npc_type_id, int grid_id, int int_unused, float X, float Y, float Z, [float heading])
quest::unscribespells()
quest::untraindiscs()
quest::updatetaskactivity(int task_id, int activity_id, [int count], [bool ignore_quest_update = false])
quest::varlink(uint32 item_id)
quest::voicetell(string client_name, int macro_id, int ace_id, int gender_id)
quest::we(int emote_color_id, string message)
quest::wearchange(uint8 slot, uint16 texture_id, [uint32 hero_forge_model_id = 0], [uint32 elite_material_id = 0])
quest::worldwidemarquee(uint32 color_id, uint32 priority, uint32 fade_in, uint32 fade_out, uint32 duration, string message)
quest::write(string file_name, string message)
quest::ze(int emote_color_id, string message)
quest::zone(string zone_name)
quest::zonegroup(string zone_name)
quest::zoneraid(string zone_name)
```
{% endtab %}

{% tab title="Lua" %}
```lua
eq.active_speak_activity(int task_id); -- int
eq.active_speak_task(); -- int
eq.active_tasks_in_set(int task_set); -- int
eq.add_area(int id, int type, float min_x, float max_x, float min_y, float max_y, float min_z, float max_z); -- void
eq.assign_group_to_instance(uint32 instance_id); -- void
eq.assign_raid_to_instance(uint32 instance_id); -- void
eq.assign_task(int task_id); -- void
eq.assign_to_instance(uint32 instance_id); -- void
eq.assign_to_instance_by_char_id(uint32 instance_id, uint32 char_id); -- void
eq.attack(const char *client_name); -- void
eq.attack_npc(int entity_id); -- void
eq.attack_npc_type(int npc_type); -- void
eq.bury_player_corpse(uint32 char_id); -- bool
eq.check_instance_id_by_char_id(uint16 instance_id, uint32 char_id); -- bool
eq.check_title(uint32 title_set); -- void
eq.clear_areas(); -- void
eq.clear_npctype_cache(int npctype_id); -- void
eq.clear_opcode(int op); -- void
eq.clear_proximity(); -- void
eq.clear_spawn_timers(); -- void
eq.clock(); -- double
eq.collect_items(uint32 item_id, bool remove); -- int
eq.completed_tasks_in_set(int task_set); -- int
eq.count_item(uint32 item_id); -- int
eq.create_door(const char *model, float x, float y, float z, float h, int open_type, int size); -- void
eq.create_ground_object(uint32 item_id, float x, float y, float z, float h); -- void
eq.create_ground_object(uint32 item_id, float x, float y, float z, float h, uint32 decay_time); -- void
eq.create_ground_object_from_model(const char *model, float x, float y, float z, float h); -- void
eq.create_ground_object_from_model(const char *model, float x, float y, float z, float h, int type); -- void
eq.create_ground_object_from_model(const char *model, float x, float y, float z, float h, int type, uint32 decay_time); -- void
eq.create_guild(const char *name, const char *leader); -- void
eq.create_instance(const char *zone, uint32 version, uint32 duration); -- uint32
eq.cross_zone_assign_task_by_char_id(int character_id, uint32 task_id); -- void
eq.cross_zone_assign_task_by_char_id(int character_id, uint32 task_id, bool enforce_level_requirement); -- void
eq.cross_zone_assign_task_by_group_id(int group_id, uint32 task_id); -- void
eq.cross_zone_assign_task_by_group_id(int group_id, uint32 task_id bool enforce_level_requirement); -- void
eq.cross_zone_assign_task_by_raid_id(int raid_id, uint32 task_id); -- void
eq.cross_zone_assign_task_by_raid_id(int raid_id, uint32 task_id bool enforce_level_requirement); -- void
eq.cross_zone_assign_task_by_guild_id(int guild_id, uint32 task_id); -- void
eq.cross_zone_assign_task_by_guild_id(int guild_id, uint32 task_id, bool enforce_level_requirement); -- void
eq.cross_zone_message_player_by_name(uint32 type, const char *player, const char *message); -- void
eq.cross_zone_message_player_by_group_id(uint32 type, int group_id, const char *message); -- void
eq.cross_zone_message_player_by_raid_id(uint32 type, int raid_id *player, const char *message); -- void
eq.cross_zone_message_player_by_guild_id(uint32 type, int guild_id, const char *message); -- void
eq.cross_zone_move_player_by_char_id(int character_id, const char *zone_short_name); -- void
eq.cross_zone_move_player_by_group_id(int group_id, const char *zone_short_name); -- void
eq.cross_zone_move_player_by_raid_id(int raid_id, const char *zone_short_name); -- void
eq.cross_zone_move_player_by_guild_id(int guild_id, const char *zone_short_name); -- void
eq.cross_zone_set_entity_variable_by_client_name(const char *player, const char *id, const char *m_var); -- void
eq.cross_zone_set_entity_variable_by_group_id(int group_id, const char *id, const char *m_var); -- void
eq.cross_zone_set_entity_variable_by_raid_id(int raid_id, const char *id, const char *m_var); -- void
eq.cross_zone_set_entity_variable_by_guild_id(int guild_id, const char *id, const char *m_var); -- void
eq.cross_zone_signal_client_by_char_id(uint32 player_id, int signal); -- void
eq.cross_zone_signal_client_by_name(const char *player, int signal); -- void
eq.cross_zone_signal_client_by_group_id(int group_id, int signal); -- void
eq.cross_zone_signal_client_by_raid_id(int raid_id, int signal); -- void
eq.cross_zone_signal_client_by_guild_id(int guild_id, int signal); -- void
eq.debug(std::string message); -- void
eq.debug(std::string message, int level); -- void
eq.delete_data(std::string bucket_key); -- bool
eq.delete_global(const char *name); -- void
eq.depop(); -- void
eq.depop(int npc_type); -- void
eq.depop_all(); -- void
eq.depop_all(int npc_type); -- void
eq.depop_with_timer(); -- void
eq.depop_with_timer(int npc_type); -- void
eq.depop_zone(bool start_spawn_status); -- void
eq.destroy_instance(uint32 instance_id); -- void
eq.disable_proximity_say(); -- void
eq.disable_recipe(uint32 recipe_id); -- bool
eq.disable_spawn2(int spawn2_id); -- void
eq.enable_proximity_say(); -- void
eq.enable_recipe(uint32 recipe_id); -- bool
eq.enable_spawn2(int spawn2_id); -- void
eq.enable_title(uint32 title_set); -- void
eq.enabled_task_count(int task_set); -- int
eq.faction_value(); -- int
eq.fail_task(int task_id); -- void
eq.first_task_in_set(int task_set); -- int
eq.flag_instance_by_group_leader(uint32 zone, uint32 version); -- void
eq.flag_instance_by_raid_leader(uint32 zone, uint32 version); -- void
eq.fly_mode(int flymode); -- void
eq.follow(int entity_id); -- void
eq.follow(int entity_id, int distance); -- void
eq.get_char_name_by_id(uint32 char_id); -- std::string
eq.get_char_id_by_name(string name); -- int
eq.get_class_name(uint8 class_id, uint8 level); -- std::string
eq.get_currency_id(uint32 item_id); -- int
eq.get_currency_item_id(int currency_id); -- int
eq.get_data(std::string bucket_key); -- std::string
eq.get_data_expires(std::string bucket_key); -- std::string
eq.get_encounter(); -- std::string
eq.get_entity_list(); -- Lua_EntityList
eq.get_initiator(); -- Lua_Client
eq.get_instance_id(const char *zone, uint32 version); -- int
eq.get_instance_id_by_char_id(const char *zone, uint32 version, uint32 char_id); -- int
eq.get_instance_timer(); -- uint32
eq.get_instance_timer_by_id(uint16 instance_id); -- uint32
eq.get_item_name(uint32 item_id) -- std::string
eq.get_level(int type); -- int
eq.get_npc_name_by_id(uint32 npc_id); -- std::string
eq.get_owner(); -- Lua_Mob
eq.get_player_buried_corpse_count(uint32 char_id); -- int
eq.get_player_corpse_count(uint32 char_id); -- int
eq.get_player_corpse_count_by_zone_id(uint32 char_id, uint32 zone_id); -- int
eq.get_quest_item(); -- Lua_ItemInst
eq.get_race_name(uint16 race_id) -- std::stringgeq.get_rule(std::string rule_name); -- std::string
eq.get_spawn_condition(const char *zone, uint32 instance_id, int condition_id); -- int
eq.get_skill_name(int skill_id); -- std::string
eq.get_spell_name(uint32 spell_id); -- std::string
eq.get_task_activity_done_count(int task, int activity); -- int
eq.get_task_name(uint32 task_id); -- std::string
eq.get_zone_id(); -- int
eq.get_zone_instance_id(); -- int
eq.get_zone_instance_version(); -- int
eq.get_zone_weather(); -- int
eq.is_disc_tome(int item_id); -- bool
eq.is_paused_timer(const char *timer); -- bool
eq.is_task_active(int task); -- bool
eq.is_task_activity_active(int task, int activity); -- bool
eq.is_task_appropriate(int task); -- bool
eq.is_task_completed(int task_id); -- int
eq.is_task_enabled(int task); -- bool
eq.item_link(int item_id); -- std::string
eq.last_task_in_set(int task_set); -- int
eq.map_opcodes(); -- void
eq.merchant_count_item(uint32 npc_id, uint32 item_id); -- int
eq.merchant_set_item(uint32 npc_id, uint32 item_id); -- void
eq.merchant_set_item(uint32 npc_id, uint32 item_id, uint32 quantity); -- void
eq.modify_npc_stat(const char *id, const char *value); -- void
eq.move_to(float x, float y, float z); -- void
eq.move_to(float x, float y, float z, float h); -- void
eq.move_to(float x, float y, float z, float h, bool save_guard_spot); -- void
eq.next_task_in_set(int task_set, int task_id); -- int
eq.path_resume(); -- void
eq.pause(int duration); -- void
eq.pause_timer(const char *timer); -- void
eq.popup(const char *title, const char *text, uint32 id, uint32 buttons, uint32 duration); -- void
eq.rain(int weather); -- void
eq.reloadzonestaticdata(); -- void
eq.remove_all_from_instance(uint32 instance_id); -- void
eq.remove_area(int id); -- void
eq.remove_from_instance(uint32 instance_id); -- void
eq.remove_from_instance_by_char_id(uint32 instance_id, uint32 char_id); -- void
eq.remove_spawn_point(uint32 spawn2_id); -- void
eq.remove_title(uint32 title_set); -- void
eq.repop_zone(); -- void
eq.reset_task_activity(int task, int activity); -- void
eq.respawn(int npc_type, int grid); -- void
eq.resume_timer(const char *timer); -- void
eq.safe_move(); -- void
eq.say_link(const char *phrase); -- std::string
eq.say_link(const char *phrase, bool silent); -- std::string
eq.say_link(const char *phrase, bool silent, const char *link_name); -- std::string
eq.scribe_spells(int max); -- int
eq.scribe_spells(int max, int min); -- int
eq.send_mail(const char *to, const char *from, const char *subject, const char *message); -- void
eq.set_anim(int npc_type, int anim_num); -- void
eq.set_data(std::string bucket_key, std::string bucket_value); -- void
eq.set_data(std::string bucket_key, std::string bucket_value, std::string expires_at); -- void
eq.set_global(const char *name, const char *value, int options, const char *duration); -- void
eq.set_guild(int guild_id, int rank); -- void
eq.set_next_hp_event(int hp); -- void
eq.set_next_inc_hp_event(int hp); -- void
eq.set_proximity(float min_x, float max_x, float min_y, float max_y); -- void
eq.set_proximity(float min_x, float max_x, float min_y, float max_y, float min_z, float max_z); -- void
eq.set_proximity(float min_x, float max_x, float min_y, float max_y, float min_z, float max_z, bool say); -- void
eq.set_rule(std::string rule_name, std::string rule_value); -- void
eq.set_sky(int sky); -- void
eq.set_time(int hour, int min); -- void
eq.set_time(int hour, int min, bool update_world); -- void
eq.set_timer(const char *timer, int time_ms); -- void
eq.set_timer(const char *timer, int time_ms, Lua_Encounter enc); -- void
eq.set_timer(const char *timer, int time_ms, Lua_ItemInst inst); -- void
eq.set_timer(const char *timer, int time_ms, Lua_Mob mob); -- void
eq.signal(int npc_id, int signal_id); -- void
eq.signal(int npc_id, int signal_id, int wait); -- void
eq.snow(int weather); -- void
eq.spawn2(int npc_type, int grid, int unused, double x, double y, double z, double heading); -- Lua_Mob
eq.spawn_condition(const char *zone, uint32 instance_id, int condition_id, int value); -- void
eq.spawn_from_spawn2(uint32 spawn2_id); -- Lua_Mob
eq.start(int wp); -- void
eq.stop(); -- void
eq.stop_all_timers(); -- void
eq.stop_all_timers(Lua_Encounter enc); -- void
eq.stop_all_timers(Lua_ItemInst inst); -- void
eq.stop_all_timers(Lua_Mob mob); -- void
eq.stop_follow(); -- void
eq.stop_timer(const char *timer); -- void
eq.stop_timer(const char *timer, Lua_Encounter enc); -- void
eq.stop_timer(const char *timer, Lua_ItemInst inst); -- void
eq.stop_timer(const char *timer, Lua_Mob mob); -- void
eq.summon_all_player_corpses(uint32 char_id, float x, float y, float z, float h); -- void
eq.summon_buried_player_corpse(uint32 char_id, float x, float y, float z, float h); -- void
eq.target_global(const char *name, const char *value, const char *duration, int npc_id, int char_id, int zone_id); -- void
eq.task_explored_area(int explore_id); -- void
eq.task_set_selector(int task_set); -- void
eq.task_time_left(int task_id); -- int
eq.toggle_spawn_event(int event_id, bool enable, bool strict, bool reset); -- void
eq.train_discs(int max); -- int
eq.train_discs(int max, int min); -- int
eq.unique_spawn(int npc_type, int grid, int unused, double x, double y, double z, double heading = 0.0); -- Lua_Mob
eq.update_instance_timer(uint16 instance_id, uint32 new_duration); -- void
eq.update_spawn_timer(uint32 id, uint32 new_time); -- void
eq.update_task_activity(int task, int activity, int count); -- void
eq.update_zone_header(std::string type, std::string value); -- void
eq.voice_tell(const char *str, uint32 macro_num, uint32 race_num, uint32 gender_num); -- void
eq.wear_change(uint32 slot, uint32 texture); -- void
eq.world_emote(int type, const char *str); -- void
eq.world_wide_marquee(uint32 type, uint32 priority, uint32 fadein, uint32 fadeout, uint32 duration, const char *message); -- void
eq.zone(const char *zone_name); -- void
eq.zone_emote(int type, const char *str); -- void
eq.zone_group(const char *zone_name); -- void
eq.zone_raid(const char *zone_name); -- void
```
{% endtab %}
{% endtabs %}



### ProTip: hit ctrl + f \(Windows\) or ⌘ + f \(Mac\) to FIND something on this page



#### AssignGroupToInstance

      **Parmeter:**

      instance\_id _\(uint16\)_

      **Usage:**

      Assigns a group to an instance.

      **Example:**

```perl
#:: Create a scalar variable to store instance_id--GetInstanceID returns int
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); 
quest::AssignGroupToInstance($Instance);
```

#### AssignRaidToInstance

      **Parmeter:**

      instance\_id _\(uint16\)_

      **Usage:**

      Assigns a raid to an instance.

      **Example:**

```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); #:: GetInstanceID returns int
quest::AssignRaidToInstance($Instance);
```

#### AssignToInstance

      **Parameter:**

      instance\_id _\(uint16\)_

      **Usage:**

      Assigns a single player to an instance.

      **Example**

```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); #:: GetInstanceID returns int
quest::AssignToInstance($Instance);
```

#### AssignToInstanceByCharID

      **Parameter:**

      instance\_id _\(uint16\)_, char\_id _\(uint32\)_

      **Usage:**

      Assigns a single player to an instance by character ID.

      **Example**

```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceIDByCharID($zonesn, $instanceversion, $charid); #:: Returns int
quest::AssignToInstanceByCharID($Instance, $charid);
```

#### ChooseRandom

      **Parameter\(s\):**

      option1, option2, option3...

      **Usage:**

      Returns one of the items listed in its arguments randomly.

      **Example:**

```perl
#:: Choose a random reward: 1001 - Cloth Cap, 1004 - Cloth Shirt, 1011 - Cloth Pants
quest::summonitem(quest::ChooseRandom(1001, 1004, 1011);
```

#### CreateInstance

      **Parameter\(s\):**

      zone\_name _\(string\)_, version _\(uint16\)_, duration _\(uint32\)_

      **Usage:**

      Creates an instance in the given zone using specified version and duration.

      **Example:**

```perl
quest::CreateInstance("mirb", 50, 10800);
```

#### DestroyInstance

      **Parameter\(s\):**

      instance\_id _\(uint16\)_

      **Usage:**

      Destroys the given instance.

      **Example:**

```perl
quest::DestroyInstance(50);
```

#### FlagInstanceByGroupLeader

      **Parameter\(s\):**

      zone _\(uint32\)_, version _\(uint16\)_

      **Usage:**

      Assigns the group leader's instance to a player

      **Example:**

```perl
#:: Zone 237 (mirb), instance 50
quest::FlagInstanceByGroupLeader(237,50);
```

#### FlagInstanceByRaidLeader

      **Parameter\(s\):**

      zone _\(uint32\)_, version _\(uint16\)_

      **Usage:**

      Assigns the raid leader's instance to a player

      **Example:**

```perl
#:: Zone 237 (mirb), instance 50
quest::FlagInstanceByRaidLeader(237,50);
```

#### FlyMode

      **Parameter\(s\):**

      mode \[0-3\] _\(uint8\)_

      **Usage:**

      Sets flymode for player where 0 = Off, 1 = On, 2 = Levitate.

      **Example:**

```perl
 #:: Turn fly mode on
quest::FlyMode(1);
```

#### GetCharactersInInstance

      **Parameter\(s\):**

      instance\_id _\(uint16\)_

      **Usage:**

      Returns a hash of character id and instance id

      **Example:**

```perl
#:: Instance ID 50
quest::GetCharactersInInstance(50); #:: Returns 50,123456
```

#### GetInstanceID

      **Parameter\(s\):**

      zone\_name _\(string\)_, version _\(uint16\)_

      **Usage:**

      Returns the instance id of the given zone/verison.

      **Example**

```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); #:: Returns uint16
quest::AssignToInstance($Instance);
```

#### GetInstanceIDByCharID

      **Parameter\(s\):**

      zone\_name _\(string\)_, version _\(int16\)_, char\_id _\(uint32\)_

      **Usage:**

      Returns the instance ID of the given zone and version by character ID.

      **Example**

```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceIDByCharID($zonesn, $instanceversion, $charid); #:: Returns uint16
quest::AssignToInstance($Instance);
```

#### GetInstanceTimer

      **Parameter\(s\):**

      None.

      **Usage:**

      Returns the timer for the instance.

      **Example**

```perl
quest::GetInstanceTimer(); #:: Returns uint32
```

#### GetInstanceTimerByID

      **Parameter\(s\):**

      instance\_id _\(uint16\)_

      **Usage:**

      Returns the duration timer of the specified instance.  
      Note: If you do not provide an instance\_id in the method it defaults to instance id 0 and returns 0 for time remaining.

      **Example**

```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceID($zonesn, $instanceversion); #:: Returns uint16
quest::GetInstanceTimerByID($Instance); #:: Returns timer int
```

#### GetSpellResistType

      **Parameter\(s\):**

      spell\_id _\(uint32\)_

      **Usage:**

      Returns the [Resist Type](https://github.com/EQEmu/Server/wiki/Resist-Types) of the specified spell.

      **Example**

```perl
quest::GetSpellResistType($spell_id); #:: Returns int
```

#### GetSpellTargetType

      **Parameter\(s\):**

      spell\_id _\(uint32\)_

      **Usage:**

      Returns the [Target Type](https://github.com/EQEmu/Server/wiki/Target-Types) of the specified spell.

      **Example**

```perl
quest::GetSpellTargetType($spell_id); #:: Returns int
```

#### GetTimeSeconds

      **Parameter\(s\):**

      None.

      **Usage:**

      Returns unix time in seconds.

      **Example:**

```perl
quest::GetTimeSeconds(); #:: Returns int
```

#### GetZoneID

      **Parameter\(s\):**

      zone _\(string\)_

      **Usage:**

      Returns the zone id.

      **Example:**

```perl
quest::GetZoneID($zonesn); #:: Returns int
```

#### GetZoneLongName

      **Parameter\(s\):**

      zone _\(string\)_

      **Usage:**

      Returns the long name of the zone.

      **Example:**

```perl
quest::GetZoneLongName($zonesn); #:: Returns string
```

#### IsBeneficialSpell

      **Parameter\(s\):**

      spell\_id _\(uint32\)_

      **Usage:**

      Returns true if the specified spell is beneficial.

      **Example:**

```perl
quest::IsBeneficialSpell($spell_id); #:: Returns 0 or 1
```

#### IsEffectInSpell

      **Parameter\(s\):**

      spell\_id _\(uint32\)_, effect\_id _\(uint32\)_

      **Usage:**

      Returns true if the specified spell has the specified [Spell Effect](https://github.com/EQEmu/Server/wiki/Spell-Effect-IDs).

      **Example:**

```perl
#:: Check for Spell Effect 23 - Fear
quest::IsEffectInSpell($spell_id, 23); #:: Returns 0 or 1
```

#### IsRunning

      **Parameter\(s\):**

      None.

      **Usage:**

      Returns the running state--0 is walking, 1 is running.

      **Example:**

```perl
quest::IsRunning(); #:: Returns 0 or 1
```

#### LearnRecipe

      **Parameter\(s\):**

      recipe\_id _\(uint32\)_

      **Usage:**

      Makes the client learn a recipe.

      **Example:**

```perl
#:: Teach recipe_id 2141 - Pickled Bixie
quest::LearnRecipe(2141);
```

#### MerchantCountItem

      **Parameter\(s\):**

      npc\_id _\(uint32\)_, item\_id _\(uint32\)_

      **Usage:**

      Returns the number of the specified item in stock at the specified merchant.

      **Example:**

```perl
#:: Find out how many 12260 - Fuzzlecutter Formula 5000 are in stock at Ping_Fuzzlecutter (9133)
quest::MerchantCountItem(9133, 12260); #:: Returns int
```

#### MerchantSetItem

      **Parameter\(s\):**

      npc\_id _\(uint32\)_, item\_id _\(uint32\)_, quantity _\(uint32\)_

      **Usage:**

      Changes the number of the specified items in stock, at the specified quantity, at the specified merchant.

      **Example:**

```perl
#:: Make sure there is plenty of 12260 - Fuzzlecutter Formula 5000 in stock at Ping_Fuzzlecutter (9133)
quest::MerchantSetItem(9133, 12260, 1000); #:: Quantity 1000
```

#### ModifyNPCStat

      **Parameter\(s\):**

      key _\(string\)_, value _\(string\)_

      **Usage:**

      Changes the specified [npc\_types](https://github.com/EQEmu/Server/wiki/npc_types) stat of the specified NPC on the fly--changes are not saved to the npc\_types in the DB.

      **Example:**

```perl
#:: Adjust the runspeed to 1.25
quest::modifynpcstat("runspeed", 1.25);
```

#### MovePCInstance

      **Parameter\(s\):**

      zone\_id _\(uint32\)_, instance\_id _\(uint32\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_, heading _\(float\)_

      **Usage:**

      Moves a player to the specified instance of the specified zone at the specified location and heading.

      **Example:**

```perl
sub EVENT_CLICKDOOR {
    #:: Match door id 3: Frozen Nightmare (mirb) zone in
    if ($doorid == 3) {
        #:: Create a scalar variable to store instance_id--GetInstanceID returns int
        my $InstanceMirB = quest::GetInstanceID("mirb",50);
        #:: Match if an instance exists
        if ($InstanceMirB > 0) {
            #:: Move the player to mirb (237), to their instance, at X - 607, Y - 1503, Z - 33, Heading - 0 (north)
            quest::MovePCInstance(237,$InstanceMirB,607,1503,33,0);
        }
    }
}
```

#### RemoveAllFromInstance

      **Parameter\(s\):**

      instance\_id _\(uint16\)_

      **Usage:**

      Removes ALL players from an instance by instance ID.

      **Example:**

```perl
sub EVENT_DEATH_COMPLETE {
     #:: Instance ID is a pre-exported variable
     quest::RemoveAllFromInstance($instanceid);
}
```

#### RemoveFromInstance

      **Parameter\(s\):**

      instance\_id _\(uint16\)_

      **Usage:**

      Removes the player that triggered the event from an instance by instance ID.

      **Example:**

```perl
sub EVENT_CLICKDOOR {
     if ($doorid == 1) {
          quest::RemoveFromInstance($instanceid);
     }
}
```

#### RemoveFromInstanceByCharID

      **Parameter\(s\):**

      instance\_id _\(uint16\)_, char\_id _\(uint32\)_

      **Usage:**

      Removes a client from an instance by character ID.

      **Example:**

```perl
#:: Create a scalar variable to store instance_id
my $Instance = quest::GetInstanceIDByCharID($zonesn, $instanceversion, $charid); #:: Returns int
quest::RemoveFromInstanceByCharID($Instance, $charid);
```

#### SendMail

      **Parameter\(s\):**

      to _\(string\)_, from _\(string\)_, subject _\(string\)_, message _\(string\)_

      **Usage:**

      Used to send a mail message.

#### SetRunning

      **Parameter\(s\):**

      is\_running _\(bool\)_

      **Usage:**

      Used to toggle run/walk state.

      **Example:**

```perl
sub EVENT_SPAWN {
	#:: Set the NPC to run
	quest::SetRunning(1);
}
```

#### UpdateInstanceTimer

      **Parameter\(s\):**

      instance\_id _\(int16\)_, duration _\(uint32\)_

      **Usage:**

      Used to update a zone instance timer by instance id by the number of seconds specified.

      **Example:**

```perl
sub EVENT_CLICKDOOR {
     #:: When they open door 7...
     if ($doorid == 7) {
          #:: Add one hour of time to the current instance
          quest::UpdateInstanceTimer($instanceid,3600);
     }
}
```

#### UpdateSpawnTimer

      **Parameter\(s\):**

      spawn2\_id _\(uint32\)_, updated\_time\_till\_repop _\(uint32\)_

      **Usage:**

      Used to update a spawn timer by spawn2 ID and time specified in ms.

      **Example:**

```perl
sub EVENT_DEATH_COMPLETE {
     #:: Set a random timer on Fippy Darkpaw's spawn point
     quest::updatespawntimer(10875,(int(rand(600))+3600)*1000);
}
```

#### UpdateZoneHeader

      **Parameter\(s\):**

      key _\(string\)_, value _\(string\)_

      **Usage:**

      Allows you to manipulate zone header settings on the fly. The [Quest Manager](https://github.com/EQEmu/Server/blob/c08993b60b7b5328398459a458648a114c3fb331/zone/questmgr.cpp#L3149) lists the following possible strings: ztype, fog\_red, fog\_green, fog\_blue, fog\_minclip, fog\_maxclip, gravity, time\_type, rain\_chance, rain\_duration, snow\_chance, snow\_duration, sky, safe\_x, safe\_y, safe\_z, max\_z, underworld, minclip, maxclip, fog\_density, suspendbuffs.

      **Example:**

```perl
#:: Set the max clip plane to 500 units
quest::UpdateZoneHeader("maxclip", 500);
```

#### activespeakactivity

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Returns the Activity ID of the lowest numbered active activity to speak with an NPC in the specified task.

      **Example:**

      If you have task id 150: activity 0--kill three rats, activity 1--talk with NPC, activity 2--kill four fire beetles, activity 3--talk with NPC.

```perl
sub EVENT_SAY {
     #:: Match text for hail, case insensitive
     if ($text=~/hail/i) {
          #:: Create a scalar variable to store the current speak activity for task 150
          $speakactivity = quest::activespeakactivity(150); #:: Returns int
          #:: Match if the player is on the first speak activity
          if ($speakactivity == 1) {
               quest::say("I really hate rats.");
          }
          #:: Match if the player is on the second speak activity
          elsif ($speakactivity == 3) {
               quest::say("I really hate fire beetles.");
          }
     }
}
```

#### activespeaktask

      **Parameter\(s\):**

      None.

      **Usage:**

      Returns the Task ID of the lowest numbered task slot if the player who triggered the event has an active task with an active activity to speak to the NPC \(returns 0 if not\).

      **Example:**

      If you have task id 150: activity 0--kill three rats, activity 1--talk with NPC, activity 2--kill four fire beetles, activity 3--talk with NPC.

```perl
sub EVENT_SAY {
     #:: Match text for hail, case insensitive
     if ($text=~/hail/i) {
          #:: Create a scalar variable to store the current task that has a speak activity
          $speaktask = quest::activespeaktask(); #:: Returns int
          #:: Match if there's an active task with a speak activity
          if ($speaktask => 1) {
               quest::say("You have a task to speak with me and its ID is $speaktask.");
          }
          #:: Match if there's NO active task with a speak activity
          else {
               quest::say("You do not have any tasks with a speaking activity at this time.");
          }
     }
}
```

#### activetasksinset

      **Parameter\(s\):**

      task\_set _\(int\)_

      **Usage:**

      Returns the number of tasks in the given TaskSet that the player has active.

      **Example:**

      You have a TaskSet "20", which consists of three tasks--200, 201, 202.

```perl
sub EVENT_SAY {
     #:: Create a scalar variable to store the number of active tasks in TaskSet 20
     $activetaskcount = quest::activetasksinset(20);  #:: returns int
     #:: Match text for hail, case insensitive
     if ($text=~/hail/i) {
          quest::say("You have $activetaskcount tasks remaining.");
     }
}
```

#### addldonloss

      **Parameter\(s\):**

      losses _\(int\)_, theme\_id _\(int\)_

      **Usage:**

      Adds to loss count for LDON adventures by [LDON Theme](https://github.com/EQEmu/Server/wiki/LDON-Themes).

      **Example:**

```perl
#:: Add a loss for Rujarkian Hills theme
quest::addldonloss(1,4);
```

#### addldonpoints

      **Parameter\(s\):**

      points _\(int\)_, theme\_id _\(int\)_

      **Usage:**

      Adds to points count for LDON adventures by [LDON Theme](https://github.com/EQEmu/Server/wiki/LDON-Themes).

      **Example:**

```perl
#:: Add 100 points for Rujarkian Hills theme
quest::addldonpoints(100,4);
```

#### addldonwin

      **Parameter\(s\):**

      wins _\(int\)_, theme\_id _\(int\)_

      **Usage:**

      Adds to wins count for LDON adventures by [LDON Theme](https://github.com/EQEmu/Server/wiki/LDON-Themes).

      **Example:**

```perl
#:: Add a loss for Rujarkian Hills theme
quest::addldonwin(1,4);
```

#### addloot

      **Parameter\(s\):**

      item\_id _\(uint32\)_, charges = 0 _\(uint16\)_, equip\_item = true _\(bool\)_

      **Usage:**

      Add an item with a number of charges to an NPC's loot \(does not permanently change the loot table or lootdrop entries\). If 'equipitem' is false \(0\), the item will not be used by \(or shown in the hands of\) the NPC.

      **Example:**

```perl
#:: Add a 5013 - Rusty Short Sword to the NPC's loot, but do not equip the item
quest::addloot(5013,0,0);
```

#### addskill

      **Parameter\(s\):**

      skill\_id _\(int\)_, value _\(int\)_

      **Usage:**

      Sets the player's skill, by [Skill ID](https://github.com/EQEmu/Server/wiki/Skills), to the value specified.

      **Example:**

```perl
sub EVENT_SAY {
     #:: Match text for train, case insensitive
     if ($text=~/train/i) {
          #:: Call the custom subroutine "Train"
          Train();
     }
}

#:: Custom subroutine
sub Train {
     #:: Send a message to the client in yellow (15) text
     $client->Message( 15, "Your experiences across the realm have infused you with increased power and knowledge..." );
     #:: Set all available skills to maximum for race/class at current level
     foreach my $skill (0 .. 77) {
          #:: Continue the foreach loop using the next skill ID if the client cannot use the skill ID
          next unless $client->CanHaveSkill($skill);
          #:: Create a scalar variable to store the maximum skill Value for the Skill ID
          my $maxSkill = $client->MaxSkill($skill, $client->GetClass(), $ulevel);
          #:: Continue the foreach loop using the next Skill ID if the client has a higher skill Value for the Skill ID
          next unless $maxSkill > $client->GetRawSkill($skill);
          #:: Set the Skill ID to the maximum Value that the client is allowed
          $client->SetSkill($skill, $maxSkill);
     }
     #:: Scribe all spells for current level
     quest::scribespells($ulevel);
}
```

#### assigntask

      **Parameter\(s\):**

      task\_id _\(int\)_, npcid _\(int\)_, enforce\_level\_requirement = false _\(bool\)_

      **Usage:**

      Used to assign a task to a client, optionally this can include the NPC ID and whether or not to enforce the level requirement specified in the DB.

      **Example:**

```perl
#:: Assign Task 102
quest::assigntask(102);
#:: Assign Task 103 with level requirement enforced
quest::assigntask(103, 1);
#:: Assign Task 104 and include the NPC ID
$client->AssignTask(104, $npc->GetID());
#:: Assign Task 105, include the NPC ID with level requirement enforced
$client->AssignTask(105, $npc->GetID(), 1);
```

#### attack

      **Parameter\(s\):**

      client\_name _\(string\)_

      **Usage:**

      Used to make the NPC attack a client, by name.

      **Example:**

```perl
sub EVENT_SAY {
     #:: Match text for "mother", case insensitive
     if ($text=~/mother/i) {
          quest::say("How dare you talk about my mother!");
          #:: Attack the client that triggered the event
          quest::attack($name);
     }
}
```

#### attacknpc

      **Parameter\(s\):**

      npc\_entity\_id _\(int\)_

      **Usage:**

      Used to make the NPC attack another NPC, by Entity ID.

      **Example:**

```perl
#:: Create a scalar variable to store the Entity ID of a_large_rat
$aggromob = $entity_list->GetMobID(2011);
#:: Get him.
quest::attacknpc($aggromob);
```

#### attacknpctype

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_

      **Usage:**

      Used to make the NPC attack another NPC, by NPC Type ID.

      **Example:**

```perl
#:: Attack a_large_rat
quest::attacknpctype(2011);
```

#### buryplayercorpse

      **Parameter\(s\):**

      character\_id _\(int\)_

      **Usage:**

      Buries and depops a single corpse by Character ID.

      **Example:**

```perl
sub EVENT_SAY {
     #:: Create a scalar variable for storing corpse count
     my $CorpseCount = 0;
     #:: Create a scalar variable for storing the Character ID of the Client that triggered the event
     my $charid = $client->CharacterID();
     if ($text=~/hail/i) {
          #:: Send the client a message in yellow (15) text
          $client->Message(15,"I can [bury a corpse] or [destroy a corpse] that you have unburied.");
     }
     if ($text=~/bury a corpse/i) {
          #:: Match if the client character has a corpse (or corpses)
          if ($CorpseCount > 0) {
               #:: Bury the character's corpse
               quest::buryplayercorpse($charid);
               $client->Message(15,"Very well, burying one of your corpses now.");
          }
          #:: Match if the client character does not have a corpse
          else {
               $client->Message(13,"You have no unburied corpses, begone.");
          }
     }
}
```

#### castspell

      **Parameter\(s\):**

      spell\_id _\(int\)_, target\_id _\(int\)_

      **Usage:**

      Used to make the NPC cast a spell, by ID, on a target, by ID.

      **Example:**

```perl
#:: Cast spell 12 - Healing, on the user that triggered the event
quest::castspell(12,$userid);
```

#### changedeity

      **Parameter\(s\):**

      deity\_id _\(int\)_

      **Usage:**

      Used to permanently change the client character's deity, by [Deity ID](https://github.com/EQEmu/Server/wiki/Deity-List); kicks the client to character select.

      **Example:**

```perl
#:: Change the client character's deity to 201 - Bertoxxulous
quest::changedeity(201);
```

#### checktitle

      **Parameter\(s\):**

      title\_set\_id _\(int\)_

      **Usage:**

      Used to determine if a player has the specified titleset enabled or not.

      **Example:**

```perl
#:: Check to see if Title Set 2 (prefix "Arbiter", suffix "Harbinger of the Old World") is enabled
quest::checktitle(2); #:: Returns bool
```

#### clear\_npctype\_cache

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_

      **Usage:**

      Clears the NPC Table.

#### clear\_proximity

      **Parameter\(s\):**

      None.

      **Usage:**

      Clears an NPC's defined proximity.

      **Example:**

```perl
sub EVENT_SPAWN {
     #:: Create a proximity, 50 units across
     quest::set_proximity($x - 25, $x + 25, $y - 25, $y + 25);
}

sub EVENT_ENTER {
     #:: Shout a message when the event is triggered
     quest::shout("Congratulations $name, you have won the race!");
     #:: Clear the proximity since second place is the first loser
     quest::clear_proximity();
}
```

#### clear\_zone\_flag

      **Parameter\(s\):**

      zone\_id _\(uint32\)_

      **Usage:**

      Used to clear the Zone Flag, by ID, of a client character.

      **Example:**

```perl
#:: Clear the character's Zone Flag (Sleeper's Key) for 128 - The Sleeper's Tomb (sleeper)
quest::clear_zone_flag(128);
```

#### clearspawntimers

      **Parameter\(s\):**

      None.

      **Usage:**

      Used to reset the spawn timers and repop a zone--similar to \#repop force.

      **Example:**

```perl
quest::clearspawntimers();
```

### collectitems

      **Parameter\(s\):**

      item\_id _\(int\)_, remove\_item = true _\(bool\)_

      **Usage:**

      Returns the number of items by ID that exist in inventory. If remove is true, items are removed as they are counted.

      **Example:**

```perl
sub EVENT_SAY {
	#:: Match text for "hail", case insensitive, and the client that triggered the event has a 1001 - Cloth Cap
	if ($text=~/hail/i && plugin::check_hasitem($client, 1001)) {
		quest::emote("steals your cloth cap.");
		quest::collectitems(1001, 1);
	}
}
```

### completedtasksinset

      **Parameter\(s\):**

      task\_set _\(int\)_

      **Usage:**

      Returns the number of tasks in the given Task Set that the player has completed.

      **Example:**

```perl
sub EVENT_SAY {
     #:: Match text for "tasks", case insensitive
     if ($text=~/tasks/i) {
          #:: Create a scalar variable to store the count of completed tasks in task set "200"
          my $TasksComplete = quest::completedtasksinset(200); #:: Returns int
          quest::say("You have completed $TasksComplete tasks.");
     }
}
```

### countitem

**Parameter\(s\):**

      item\_id _\(uint32\)_

      **Usage:**

      Used to return the count of a given item, by id.

      **Example:**

```perl
#:: Count the number of 1001 - Cloth Cap
quest::countitem(1001); #:: Returns Int
```

### createBot

      **Parameter\(s\):**

      first\_name _\(string\)_, last\_name _\(string\)_, level _\(int\)_, race\_id _\(int\)_, class\_id _\(int\)_, gender\_id _\(int\)_

      **Usage:**

      Used to create a bot with the given parameters.

      **Example:**

```perl
sub EVENT_ENTERZONE {
     #:: Create a bot named Leroy Jenkins, who is level 50, Human, Paladin, Male
     quest::createBot("Leroy", "Jenkins", 50, 1, 3, 0);
}
```

### createdoor

      **Parameter\(s\):**

      model\_name _\(string\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_, heading _\(float\)_, object\_type = 58 _\(int\)_, size = 100 _\(int\)_

      **Usage:**

      Creates a new door, with type 58 and size 100 as the defaults.

      **Example:**

```perl
quest::createdoor("POKTELE500", -582.532, 2324.96, -47.8143, 120, 58, 100);
```

### creategroundobject

      **Parameter\(s\):**

      item\_id _\(int\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_, heading _\(float\)_, decay\_time _\(uint32\)_

      **Usage:**

      Creates an object on the ground with the given parameters, decay time is ms = 300000 by default.

      **Example:**

```perl
sub EVENT_WAYPOINT_ARRIVE {
     #:: Create a 12274 - Chalice of Conquest at the NPC's current location
     quest::creategroundobject(12274, $x, $y, $z, $h);
}
```

### creategroundobjectfrommodel

      **Parameter\(s\):**

      model\_name _\(string\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_, heading _\(float\)_, object\_type _\(int\)_, decay\_time _\(uint32\)_

      **Usage:**

      Creates an object on the ground with the given parameters, decay time is ms = 300000 by default.

      **Example:**

```perl
#:: Create a 17330 - Bag of Supplies at the given location
quest::creategroundobjectfrommodel("IT64_ACTORDEF", 2497, -557, -327, 58, 17330);
```

### createguild

      **Parameter\(s\):**

      guild\_name _\(string\)_, leader\_name _\(string\)_

      **Usage:**

      Creates a guild.

      **Example:**

```text
sub EVENT_SAY{
     if (quest::createguild("Akkadius Fire", $client->GetName())) {
          $client->Message(15, "Guild has been created successfully");
     }
     else{
          $client->Message(15, "Guild creation error");
     }
}
```

### crosszonemessageplayerbyname

      **Parameter\(s\):**

      channel\_id _\(int\)_, name _\(string\)_, message _\(string\)_

      **Usage:**

      Sends a message to a client character on the specified channel. Useful for Expeditions and Shared Tasks.

      **Example:**

```text
quest::crosszonemessageplayerbyname(15, $name, "Hi.");
```

### crosszonesetentityvariablebyclientname

      **Parameter\(s\):**

      client\_name _\(string\)_, key _\(string\)_, value _\(string\)_

      **Usage:**

      Sets entity variables world-wide for the provided client character.

### crosszonesetentityvariablebynpctypeid

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_, key _\(string\)_, value _\(string\)_

      **Usage:**

      Sets entity variables world wide with specified npctype\_id.

### crosszonesignalclientbycharid

      **Parameter\(s\):**

      character\_id _\(int\)_, value _\(int\)_

      **Usage:**

      Signals the client by character ID world wide.

      **Example:**

```text
#:: Signal the client character who triggered the event with "5000"
quest::crosszonesignalclientbycharid($charid,5000);
```

### crosszonesignalnpcbynpctypeid

      **Parameter\(s\):**

      npc\_type\_id _\(uint32\)_, value _\(uint32\)_

      **Usage:**

      Signals all NPC entities world-wide with the specified value.

      **Example:**

```text
#:: Signal all 4036 - a_giant_rat with "99"
quest::crosszonesignalnpcbynpctypeid(4036, 99);
```

### debug

      **Parameter\(s\):**

      message _\(string\)_, debug\_level _\(uint8\)_

      **Usage:**

      Allows you to export debug information for an event, at the specified level \(1 through 3\).

      **Example:**

```text
sub EVENT_ENVIRONMENTAL_DAMAGE {
     quest::debug("EVENT_ENVIRONMENTAL_DAMAGE");
     quest::debug("env_damage is " . $env_damage);
     quest::debug("env_damage_type is " . $env_damage_type);
     quest::debug("env_final_damage is " . $env_final_damage);
}
```

### delglobal

      **Parameter\(s\):**

      key _\(string\)_

      **Usage:**

      Deletes a quest global. Please consider using [Data Buckets](https://github.com/EQEmu/Server/wiki/Data-Buckets) instead of quest globals.

      **Example:**

```text
quest::delglobal("strongbox");
```

### depop

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_

      **Usage:**

      Depops an NPC by npc\_type\_id, default is 0 \(self\).

      **Example:**

```text
#:: Depop self
quest::depop();
```

### depop\_withtimer

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_

      **Usage:**

      Depops an NPC by npc\_type\_id, default is 0 \(self\), and restarts the spawn point timer.

      **Example:**

```text
#:: Depop self and restart spawn timer
quest::depop_withtimer();
```

### depopall

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_

      **Usage:**

      Depops all NPC entities with npc\_type\_id in the zone. Default is 0 \(self and others like me\).

      **Example:**

```text
#:: Depop all 4036 - a_giant_rat
quest::depopall(4036);
```

### depopzone

      **Parameter\(s\):**

      start\_spawn\_status _\(bool\)_

      **Usage:**

      Depops the zone with the specified parameter. Default is false \(don't start spawn timers\).

      **Example:**

```text
#:: Depop the zone and don't start the spawn timers
quest::depopzone();
```

### ding

      **Parameter\(s\):**

      None.

      **Usage:**

      Plays the beautiful ding sound, the trumpet fanfare for your glorious deeds. Congratulations, winner. You did it.

      **Example:**

```text
#:: Ding!
quest::ding();
```

### disable\_proximity\_say

      **Parameter\(s\):**

      None.

      **Usage:**

      Disables proximity say for the NPC. Proximity say must be enabled with quest::set\_proximity\(\); and quest::enable\_proximity\_say\(\);.

      **Example:**

```text
quest::disable_proximity_say();
```

### disable\_spawn2

      **Parameter\(s\):**

      spawn2\_id _\(int\)_

      **Usage:**

      Disables the spawn point specified and depops any NPC entity from that spawn point.

      **Example:**

```text
#:: Disable the spawn point for 151562 - spawngroup ID 113004 - npcIDs 15138 (Droon) and 15160 (Proon)
quest::disable_spawn2(151562);
```

### disablerecipe

      **Parameter\(s\):**

      recipe\_id _\(int\)_

      **Usage:**

      Disables the recipe specified by Recipe ID.

      **Example:**

```text
#:: Disable recipe 1 - Blessed Fishing Rod
quest::disablerecipe(1);
```

### disabletask

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Disables a task so that it is not available to a client character. Useful if you do not want someone to repeat a task.

      **Example:**

```text
#:: Match if the player has an active task
if ($task != 0) {
     #:: Create a scalar variable to store the active speak-to activity
     $activity = quest::activespeakactivity($task);
     #:: Mark the activity as complete
     quest::updatetaskactivity($task, $activity);
     quest::say("Well done!");
     #:: Offer the next task, if there is one
     if (!quest::istaskactive($task)) {
          #:: Disable the task so that it cannot be repeated
          quest::disabletask($task);
          #:: Match if there are tasks remaining in the Task Set
          if ($task != quest::lasttaskinset(200)) {
               quest::say("Well done, I have another task if you are willing.");
               #:: Enable the next Task in the Task Set
               quest::enabletask(quest::nexttaskinset(200, $task));
          }
          #:: Match if there are no tasks remaining in the task set
          else {
               quest::say("Thank you for cleansing Qeynos Hills!");
          }
     }
}
```

### doanim

      **Parameter\(s\):**

      animation\_id _\(int\)_

      **Usage:**

      Makes the NPC perform the indicated [Animation](https://github.com/EQEmu/Server/wiki/Animations).

      **Example:**

```text
#:: Perform the Cheer animation
quest::doanim(27);
```

quest::echo

      **Parameter\(s\):**

      emote\_color\_id _\(int\)_, message _\(string\)_

      **Usage:**

      Echoes the specified message string, in the specified color, to the client console.

      **Example:**

```text
#:: Echo a message in yellow text (15)
quest::echo(15,"Hello, world");
```

### emote

      **Parameter\(s\):**

      message _\(string\)_

      **Usage:**

      Makes the NPC emote the specified message string.

      **Example:**

```text
sub EVENT_DEATH_COMPLETE {
     quest::emote("'s corpse says 'How...did...ugh...'");
}
```

### enable\_proximity\_say

      **Parameter\(s\):**

      None.

      **Usage:**

      Enables proximity say for the NPC--the target would not have to have the NPC targeted to interact if the NPC has a defined proximity and proximity say is enabled.

      **Example:**

```text
sub EVENT_SPAWN {
	#:: Create a proximity, 100 units across, 100 units tall, enable proximity say
	quest::set_proximity($x - 50, $x + 50, $y - 50, $y + 50, $z - 50, $z + 50, 1);
	#:: Also, enable proximity say
	quest::enable_proximity_say();
}

sub EVENT_PROXIMITY_SAY {
     if ($text=~/Ganelorn Oast/i) {
          quest::say("Ganelorn Oast! For he has single-handedly caught more poachers than any other ranger. He is credited for helping numerous endangered species recover from certain extinction. I suppose I am lucky he is fond of my sister, as I am soon to train under him as an apprentice. Perhaps one day I will even [" . quest::saylink("call upon the flames") . "] in the way that he does.");
     }
     elsif ($text=~/call upon the flames/i) {
          quest::say("Aye, Ganelorn is renowned not only for his abilities as an archer and a master of melee combat, but also for his use of powerful magics. Never before have I seen a forester evoke a fireball of such great force. It would be any ranger's dream to become his pupil just to study that one spell. Ganelorn doesn't train just anyone, though. If you want to learn from him, I'm certain you would have to prove yourself as a forester.");
     }
     if ($text=~/I want to learn/i) {
          quest::say("He is a very busy individual. I believe he is currently in the eastern part of the Karanas trying to track down a poacher. Even if you can track him down, don't get your hopes up.");
          #:: Send a signal 2 to The Greater Faydark >> Lily_Ashwood (54086)
          quest::signalwith(54086, 2, 3);
     }
}
```

### enable\_spawn2

      **Parameter\(s\):**

      spawn2\_id _\(int\)_

      **Usage:**

      Enables the specified spawn point.

      **Example:**

```text
sub EVENT_DEATH_COMPLETE {
     #:: Enable the spawn timer for 151562 - spawngroup ID 113004 - npcIDs 15138 (Droon) and 15160 (Proon)
     quest::enable_spawn2(151562);
}
```

### enabledtaskcount

      **Parameter\(s\):**

      task\_set _\(int\)_

      **Usage:**

      Counts the enabled tasks in the specified Task Set.

      **Example:**

```text
#:: Match if there are no enabled tasks in Task Set 10
if (quest::enabledtaskcount(10) == 0) {
     quest::enabletask(50, 51, 52);
}
```

### enablerecipe

      **Parameter\(s\):**

      recipe\_id _\(int\)_

      **Usage:**

      Enables the recipe specified by Recipe ID.

      **Example:**

```text
#:: Enable recipe 1 - Blessed Fishing Rod
quest::enablerecipe(1);
```

### enabletask

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Enables a task.

      **Example:**

```text
#:: Match if the player has an active task
if ($task != 0) {
     #:: Create a scalar variable to store the active speak-to activity
     $activity = quest::activespeakactivity($task);
     #:: Mark the activity as complete
     quest::updatetaskactivity($task, $activity);
     quest::say("Well done!");
     #:: Offer the next task, if there is one
     if (!quest::istaskactive($task)) {
          #:: Disable the task so that it cannot be repeated
          quest::disabletask($task);
          #:: Match if there are tasks remaining in the Task Set
          if ($task != quest::lasttaskinset(200)) {
               quest::say("Well done, I have another task if you are willing.");
               #:: Enable the next Task in the Task Set
               quest::enabletask(quest::nexttaskinset(200, $task));
          }
          #:: Match if there are no tasks remaining in the task set
          else {
               quest::say("Thank you for cleansing Qeynos Hills!");
          }
     }
}
```

### enabletitle

      **Parameter\(s\):**

      title\_set\_id _\(int\)_

      **Usage:**

      Enables the specified Title Set.

      **Example:**

```text
sub EVENT_ITEM_CLICK {
     #:: Match if item 98471 - Mastering Tinkering Master I is clicked
     if ($itemid == 98471) {
          #:: Tinkering Mastery AA ID 575 Rank 1
          $client->GrantAlternateAdvancementAbility(575,1,0);
          #:: Send a message in Yellow (15) text
          $client->Message(15,"You have mastered tinkering!");
          #:: Ding!
          quest::ding();
          #:: Enable tinkering mastery title set
          quest::enabletitle(10);
     } 
}
```

### exp

      **Parameter\(s\):**

      amount _\(int\)_

      **Usage:**

      Gives the amount of [experience](https://github.com/EQEmu/Server/wiki/Experience-by-Level) specified to the client character.

      **Example:**

```text
#:: Grant 100 experience points
quest::exp(100);
```

### faction

      **Parameter\(s\):**

      faction\_id _\(int\)_, value _\(int\)_, temp _\(int\)_

      **Usage:**

      Gives the client character the faction, specified by Faction ID, in the amount specified by value. Temp is optional, and defaults to 0. Temp values are: 0 \(permanent, with a message\), 1 \(temporary, without a message\), 2 \(temporary, with a message\), or 3 \(permanent, without a message\).

      **Example:**

```text
#:: Set faction
quest::faction(192,10); 	#:: +10 League of Antonican Bards
quest::faction(184,10); 	#:: +10 Knights of Truth
quest::faction(135,10); 	#:: +10 Guards of Qeynos
quest::faction(273,-30); 	#:: -30 Ring of Scale
```

### factionvalue

      **Parameter\(s\):**

      None.

      **Usage:**

      Returns faction values for the client character that triggered the event. Generally the opposite values of $faction, with 1 being "scowls" and 9 being "ally" \($faction considers 1 to be "ally", and 9 "scowls"\).

      **Example:**

```text
sub EVENT_SAY {
     if ($text=~/hail/i) {     
          #:: Create a scalar variable for storing faction
          my $backwardfaction = quest::factionvalue();  #:: Returns int
          quest::say("Your faction is $faction, but your faction is $backwardfaction");  #:: $faction is pre-exported and returns int
     }
}
```

### failtask

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Fails the task, by Task ID, for the client character that triggered the event.

      **Example:**

```text
#:: Fail Task 216
quest::failtask(216);
```

### firsttaskinset

      **Parameter\(s\):**

      task\_set _\(int\)_

      **Usage:**

      Returns the first task in the specified Task Set.

      **Example:**

```text
sub EVENT_SAY {
     #:: If the player hasn't completed the last task in the Task Set
     if (!quest::istaskcompleted(quest::lasttaskinset(200))) {
          #:: If the player has no tasks enabled for this task set, enable the first one
          if (quest::enabledtaskcount(200) == 0) {
               quest::say("You have not done any of my tasks before!");
               #:: Enable the first task in Task Set 200
               quest::enabletask(quest::firsttaskinset(200));
          }
     }
}
```

### follow

      **Parameter\(s\):**

      entity\_id _\(int\)_, distance _\(int\)_

      **Usage:**

      Used to make an NPC follow another NPC, specified by Entity ID. The distance determines how many units the NPC will follow behind the specified NPC, with a default value of 10; distance is optional.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Create a timer that triggers every 10 seconds
     quest::settimer("follow",10);
}

sub EVENT_TIMER {
     #:: Match if the timer is named "follow"
     if ($timer eq "follow") {
          #:: Create a scalar variable to store the NPC Type ID for mob 2161
          my $getmobbynpctype = $entity_list->GetMobByNpcTypeID(2161);
          #:: Create a scalar variable to store the Entity ID of the aforementioned NPC
          my $follow_target = $getmobbynpctype->GetID();
          #:: Follow the NPC at a default distance of 10 units
          quest::follow($follow_target);
          #:: Clean up and stop the timer
          quest::stoptimer("follow");
     }
}
```

### forcedoorclose

      **Parameter\(s\):**

      door\_id _\(int\)_, alt\_mode _\(bool\)_

      **Usage:**

      Forces a door, by Door ID, to close. Alt\_Mode is default false.

      **Example:**

```text
#:: Close Door ID 31 in Befallen
quest::forcedoorclose(31);
```

### forcedooropen

      **Parameter\(s\):**

      door\_id _\(int\)_, alt\_mode _\(bool\)_

      **Usage:**

      Forces a door, by Door ID, to open. Alt\_Mode is default false.

      **Example:**

```text
#:: Open Door ID 31 in Befallen
quest::forcedooropen(31);
```

### get\_rule

      **Parameter\(s\):**

      rule\_name _\(string\)_

      **Usage:**

      Returns the value of the specified [Rule](https://github.com/EQEmu/Server/wiki/Server-Rules) for the zone you're in.

      **Example:**

```text
#:: Get the rule value for rule "Zone:UseZoneController"
sub EVENT_SAY {
	if ($text=~/Hail/i) {
		plugin::Whisper(quest::get_rule("Zone:UseZoneController")); #:: Whispers rule value to client.
	}
}
```

### get\_spawn\_condition

      **Parameter\(s\):**

      zone\_short _\(string\)_, instance\_id _\(int\)_, condition\_id _\(int\)_

      **Usage:**

      Returns the value of the specified spawn condition.

      **Example:**

```text
#:: Get the Spawn Condition for Condition ID 1, in the default instance of Lesser Faydark
quest::get_spawn_condition("lfaydark", 0, 1);  #:: Returns int
```

### getguildnamebyid

      **Parameter\(s\):**

      guild\_id _\(uint32\)_

      **Usage:**

      Returns the name of the Guild for the specified Guild ID.

      **Example:**

```text
sub EVENT_CONNECT {
     #:: Announce the name of the client character that triggered the event in GM Say
     quest::gmsay("$name has connected.", 18, 1);
     #:: Announce the Account Name of the client character that triggered the event in GM Say
     quest::gmsay(" Account Name: " . $client->AccountName() . " - Status: $status", 18, 1);
     #:: Match if the client character has a guild
     if ($uguild_id > 0) {
          #:: Create a scalar variable to store the name of the client character's guild
          my $guildname = quest::getguildnamebyid($uguild_id);
          #:: Announce the client character's information in GM Say
          quest::gmsay("(Character Profile: Level $ulevel $race $class) <$guildname>)", 18, 1);
     }
     #:: Match if the client character does not have a guild
     else {
          #:: Announce the client character's information in GM Say
          quest::gmsay("(Character Profile: Level $ulevel $race $class) <No Guild>", 18, 1);
     }
}
```

### getitemname

      **Parameter\(s\):**

      item identifier _\(uint32\)_

      **Usage:**

      Returns the Item Name for the specified item identifier. Note that $itemname is not globally exported.

      **Example:**

```text
sub EVENT_ITEM {
	#:: Match a 1001 - Cloth Cap
	if (plugin::takeItems(1001 => 1)) {
		$ItemName = quest::getitemname(1001);
		quest::say("Thank you for the $ItemName.")
	}
	#:: Return unused items
	plugin::returnUnusedItems();
}
```

### getinventoryslotid

      **Parameter\(s\):**

      identifier _\(string\)_

      **Usage:**

      Returns the Inventory Slot ID for the specified identifier. Reference [Perl Inventory Slot Identifiers](https://github.com/EQEmu/Server/wiki/Perl-Inventory-Slot-Identifiers) for appropriate identifier tokens.

      **Example:**

```text
#:: Create a scalar variable to store an item ID
my $charmitem = $client->GetItemIDAt(quest::getinventoryslotid("charm"));  #:: returns int
```

### getlevel

      **Parameter\(s\):**

      type _\(int\)_

      **Usage:**

      Returns the level for the Type specified. Types can be 0 \(self\), 1 \(group average\), 2 \(raid average\), 3 \(raid average, group average, or self\), or 4 \(self level 2--the highest level attained by self\).

      **Example:**

```text
#:: Get the level of the client character
quest::getlevel(0);  #:: Returns int
```

### getplayerburiedcorpsecount

      **Parameter\(s\):**

      character\_id _\(int\)_

      **Usage:**

      Returns the number of corpses for the specified Character ID that are buried.

      **Example:**

```text
#:: Get the number of burried corpses for character ID 12345
quest::getplayerburriedcorpsecount(12345); #:: return int
```

### getspellname

      **Parameter\(s\):**

      spell\_id _\(uint32\)_

      **Usage:**

      Returns the name of the spell, by spell identifier.

      **Example:**

```text
sub EVENT_CAST {
    $SpellName = quest::getspellname($spell_id);
    quest::ze("$name cast the spell:  $spell_id - $SpellName.");
} 
```

### gettaskactivitydonecount

      **Parameter\(s\):**

      task\_id _\(int\)_, activity\_id _\(int\)_

      **Usage:**

      Returns the task activity done count, by Task ID and Activity ID, for the client entity.

      **Example:**

```text
#:: Find out how many times the client character has killed 10 beetles in Unrest
quest::gettaskactivitydonecount(15,3);  #:: Returns int
```

### 

### gettaskname

      **Parameter\(s\):**

      task\_id _\(uint32\)_

      **Usage:**

      Returns the task name, by Task ID, for the client entity.

      **Example:**

```text
#:: Match task 1 - kill some rats
$TaskName = quest::gettaskname(1);
quest::say("Your current task is:  $TaskName");
```

### givecash

      **Parameter\(s\):**

      copper _\(int\)_, silver _\(int\)_, gold _\(int\)_, platinum _\(int\)_

      **Usage:**

      Gives the specified amount of money to the client that triggered the event.

      **Example:**

```text
#:: Create a hash for storing cash - 20 to 100cp
my %cash = plugin::RandomCash(20,100);
#:: Grant a random cash reward
quest::givecash($cash{copper},$cash{silver},$cash{gold},$cash{platinum});
```

### gmmove

      **Parameter\(s\):**

      x _\(float\)_, y _\(float\)_, z _\(float\)_

      **Usage:**

      Moves the entity to the specified coordinates.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Create a timer that loops each second
     quest::settimer("position",1);
}

sub EVENT_TIMER {
     #:: Match if the timer "position" has looped and the X and Y coordinates are outside the specified range
     if ($timer eq "position" && ($x < -353 || $x > -109 || $y < -549 || $y > -310)) {
          quest::shout("No! I must not leave the time chamber! If I do, I'll age and die!");
          #:: Move the NPC back to the chamber
          $npc->GMMove(-231.464005,-432.937469,202.375946,.125);
     }
}

sub EVENT_DEATH_COMPLETE {
     quest::stoptimer("position");
}
```

### gmsay

      **Parameter\(s\):**

      message _\(string\)_, color\_id _\(int\)_, send\_to\_world _\(bool\)_, guild\_id _\(uint32\)_, minstatus _\(\)_

      **Usage:**

      Sends a message to the client console if the parameters are met.  [Color](https://github.com/EQEmu/Server/wiki/Emote-Colors), Send to World, Guild ID, and Minimum Status are all optional, but Color defaults to 0 \(white\), Send to World defaults to 0 \(false\), and Minimum Status defaults to 80.

      **Example:**

```text
#:: Send white text to all players in the current zone with an admin status of >= 80
quest::gmsay("Text");
#:: Send yellow (15) text to all players in the current zone with an admin status of >= 80
quest::gmsay("Text", 15);
#:: Send yellow (15) text to all players with an admin status of >= 80 in all zones
quest::gmsay("Text", 15, 1);
#:: Send yellow (15) text to all players with an admin status of >= 80 in all zones, who are in a guild with a Guild ID of 30
quest::gmsay("Text", 15, 1, 30);
#:: Send yellow (15) text to all players with an admin status of >= 0 in all zones, who are in a guild with a Guild ID of 30
quest::gmsay("Text", 15, 1, 30, 0);
```

### has\_zone\_flag

      **Parameter\(s\):**

      zone\_id _\(uint32\)_

      **Usage:**

      Used to verify that a client character has the required zone flag for the specified zone.

      **Example:**

```text
sub EVENT_CLICKDOOR {
     if ($doorid == 12) {
          if (quest::has_zone_flag(200) != 1) {  #:: Returns bool
               quest::set_zone_flag(200);
          }
     }
}
```

### incstat

      **Parameter\(s\):**

      stat\_id _\(int\)_, value _\(int\)_

      **Usage:**

      Increases the specified stat by double the specified value. Stat IDs: STR = 0, STA = 1, AGI = 2, DEX = 3, INT = 4, WIS = 5, CHA = 6. Note: if you're increasing stats, the client will have to zone to see the effect.

      **Example:**

```text
#:: Increase STR by 20
quest::incstat(0, 10);
```

### isdisctome

      **Parameter\(s\):**

      item\_id _\(int\)_

      **Usage:**

      Used to check if the specified item, by Item ID, is a discipline tome. You likely have a plugin for this \(plugin::try\_tome\_handins\).

      **Example:**

```text
sub EVENT_ITEM {
     quest::traindisc($item1) if (quest::isdisctome($item1));
     quest::traindisc($item2) if (quest::isdisctome($item2));
     quest::traindisc($item3) if (quest::isdisctome($item3));
     quest::traindisc($item4) if (quest::isdisctome($item4));
}
```

### isdooropen

      **Parameter\(s\):**

      door\_id _\(int\)_

      **Usage:**

      Checks to see if the specified door is open.

      **Example:**

```text
sub EVENT_CLICKDOOR {
     my $doorcheck = quest::isdooropen(41);  #:: Returns bool
     if ($doorid == 41 && $doorcheck == 0) {
          quest::forcedooropen(41);
     }
}
```

### istaskaappropriate

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Used to see if a task is set for the appropriate level for the client character who initiated the event.

      **Example:**

```text
#:: Check if task 200 is appropriate
quest::istaskaappropriate(200);  #:: Returns bool
```

### istaskactive

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Used to determine if a task is active, by Task ID.

      **Example:**

```text
#:: Check if task 212 is active
quest::istaskactive(212); #:: Returns bool
```

### istaskactivityactive

      **Parameter\(s\):**

      task\_id _\(int\)_, activity\_id _\(int\)_

      **Usage:**

      Used to determine if a task activity is active, by Task ID and Activity ID.

      **Example:**

```text
#:: Check if Activity 9 of Task 212 is active 
quest::istaskactivityactive(212, 9); #:: Returns bool
```

### istaskcompleted

      **Parameter\(s\):**

      task\_id \(int\)

      **Usage:**

      Used to determine if a task is completed, by Task ID.

      **Example:**

```text
#:: Check if task 212 is completed
quest::istaskcompleted(212); #:: Returns bool
```

### istaskenabled

      **Parameter\(s\):**

      task\_id \(int\)

      **Usage:**

      Used to determine if a task is enabled, by Task ID.

      **Example:**

```text
#:: Check if task 212 is enabled
quest::istaskenabled(212); #:: Returns bool
```

### itemlink

      **Parameter\(s\):**

      item\_id _\(int\)_

      **Usage:**

      Used to send a link of the specified item, by Item ID.

      **Example:**

```text
#:: Send an item link for a 1001 - Cloth Cap
quest::itemlink(1001);
```

### lasttaskinset

      **Parameter\(s\):**

      task\_set _\(int\)_

      **Usage:**

      Returns the last task in the specified Task Set.

      **Example:**

```text
#:: Find the Task ID of the last task in Task Set 200
quest::lasttaskinset(200); #:: Returns int
```

### level

      **Parameter\(s\):**

      new\_level _\(int\)_

      **Usage:**

      Sets the level to the specified new level for the client character that triggered the event.

      **Example:**

```text
sub EVENT_SAY {
     if ($text=~/level/i) {
          #:: Match if user's level is 20 or under
          if ($ulevel <= 20) {
               #:: Give the player one more level
               quest::level($ulevel+1);
          }
          elsif ($ulevel >= 21) {
               $npc->CastSpell(808, $userid);
               quest::say("Begone!");
          }
     }
}
```

### me

      **Parameter\(s\):**

      message _\(string\)_

      **Usage:**

      Sends an emote without a name.

      **Example:**

```text
quest::me("This creature has no need for your money.");
```

### movegrp

      **Parameter\(s\):**

      zone\_id _\(int\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_

      **Usage:**

      Moves the group of the client character that triggered the event to the specified Zone, by Zone ID, to the location specified.

      **Example:**

```text
#:: Match text for "we are ready", case insensitive
if ($text=~/We are ready/i) {
     #:: Move the group to The Plane of Nightmares (ponightmare) at X=1194, Y=1121, Z=208
     quest::movegrp(204,1194,1121,280); 
}
```

### movepc

      **Parameter\(s\):**

      zone\_id _\(int\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_, heading _\(float\)_

      **Usage:**

      Moves the client character that triggered the event to the specified zone, by Zone ID, at the specified location. Heading is optional, but will default to 0 \(North\).

      **Example:**

```text
#:: Match text for "travel to butcherblock", case insensitive
if ($text=~/travel to butcherblock/i) {
     #:: Move the character to Butcherblock Mountains (butcher), at X=3168.92, Y=851.92, Z=11.66--the Southern dock
     quest::movepc(68,3168.92,851.92,11.66);
}
```

### moveto

      **Parameter\(s\):**

      x _\(float\)_, y _\(float\)_, z _\(float\)_, heading _\(float\)_, save\_guard\_location _\(bool\)_

      **Usage:**

      Used to move the NPC to the specified location. Heading and Save Guard Location are optional. Heading will default to 0 \(North\), and Save Guard Location will also default to 0, causing the NPC to path back. Set Save Guard Location to 1 to make the NPC stay at the moveto location.

      **Example:**

```text
sub EVENT_ITEM {
     #:: Match a 12278 - Abandoned Orc Shovel
     if (plugin::takeItems(12278 => 1)) {
          #:: 0=Stand, 1=Sit, 2=Duck, 3=Feign Death, 4=Kneel
          $npc->SetAppearance(0);
          #:: Move to the specified location and guard 
          quest::moveto(-395.87, 807.04, 70.53, 0, 1);
     }
     #:: Return unused items
     plugin::returnUnusedItems();
}
```

### nexttaskinset

      **Parameter\(s\):**

      task\_set _\(int\)_, task\_id _\(int\)_

      **Usage:**

      Returns the next task in the specified Task Set that comes after the specified Task ID.

      **Example:**

```text
sub EVENT_SAY {
     #:: Create a scalar variable to store a task integer
     $task = quest::activespeaktask();
     #:: Match if there is an active task to speak to the NPC
     if ($task != 0) {
          #:: Match if there are no active tasks for the current speaking task
          if (!quest::istaskactive($task)) {
               #:: Disable the current speaking task
               quest::disabletask($task);
               #:: Match if the current speaking task is NOT the last task in the Task Set
               if ($task != quest::lasttaskinset(200)) {
                    quest::say("Well done, I have another task if you are willing.");
                    #:: Enable the next task in Task Set 200
                    quest::enabletask(quest::nexttaskinset(200, $task));
               }
               else {
                    quest::say("Thank you for cleansing Qeynos Hills!");
               }
          }
     }
}
```

### npcfeature

      **Parameter\(s\):**

      feature _\(string\)_, value _\(int\)_

      **Usage:**

      Allows you to temporarily change the specified feature on the NPC to the specified value. Allowable features are: race, gender, texture, helm, haircolor, beardcolor, eyecolor1, eyecolor2, hair, face, beard, heritage, tatoo, details, and size.

      **Example:**

```text
#:: Change the NPC's size to 10
quest::npcfeature("size", 10);
```

### npcgender

      **Parameter\(s\):**

      gender\_id _\(int\)_

      **Usage:**

      Used to temporarily change the gender of the NPC as specified: 0 = Male, 1 = Female, 2 = Neuter.

      **Example:**

```text
#:: Change the NPC's gender to female
quest::npcgender(1);
```

### npcrace

      **Parameter\(s\):**

      race\_id _\(int\)_

      **Usage:**

      Used to temporarily change an NPC's [Race](https://github.com/EQEmu/Server/wiki/Race-Types).

      **Example:**

```text
#:: Change the NPC's Race to Golem (17)
quest::npcrace(17);
```

### npcsize

      **Parameter\(s\):**

      size _\(int\)_

      **Usage:**

      Used to temporarily change the NPC's size.

      **Example:**

```text
#:: Change the NPC's size to 17
quest::npcsize(17);
```

### npctexture

      **Parameter\(s\):**

      texture\_id _\(int\)_

      **Usage:**

      Used to temporarily change the NPC's texture.

      **Example:**

```text
#:: Change the NPC's texture to 2
quest::npctexture(2);
```

### pause

      **Parameter\(s\):**

      duration-ms _\(int\)_

      **Usage:**

      Forces the NPC to pause for the specified duration in ms.

      **Example:**

```text
#:: Pause for 1 second
quest::pause(1000);
```

### permaclass

      **Parameter\(s\):**

      class\_id _\(int\)_

      **Usage:**

      Permanently changes the class of the client character that triggered the event to the specified class, and disconnects them.

      **Example:**

```text
#:: Change class to Warrior
quest::permaclass(1);
```

### permagender

      **Parameter\(s\):**

      gender\_id _\(int\)_

      **Usage:**

      Permanently changes the gender of the client character that triggered the event to the specified gender, and disconnects them.

      **Example:**

```text
#:: Change gender 0 = Male, 1 = Female, 2 = Neuter.
quest::permagender(0);
```

### permarace

      **Parameter\(s\):**

      race\_id _\(int\)_

      **Usage:**

      Permanently changes the [Race Type](https://github.com/EQEmu/Server/wiki/Race-Types) of the client character that triggered the event to the specified race, and disconnects them.

      **Example:**

```text
#:: Change race to Human
quest::permarace(1);
```

### playerfeature

      **Parameter\(s\):**

      feature _\(string\)_, setting _\(int\)_

      **Usage:**

      Temporarily changes the player feature to the specified setting. Acceptable strings are: race, gender, texture, helm, haircolor, beardcolor, eyecolor1, eyecolor2, hair, face, beard, heritage, tattoo, details, or size.

      **Example:**

```text
#:: Change race to Human
quest::playerfeature("race", 1);
```

### playergender

      **Parameter\(s\):**

      gender\_id _\(int\)_

      **Usage:**

      Temporarily changes the gender of the client character that triggered the event to the specified gender.

      **Example:**

```text
#:: Change gender 0 = Male, 1 = Female, 2 = Neuter.
quest::playergender(0);
```

### playerrace

      **Parameter\(s\):**

      race\_id _\(int\)_

      **Usage:**

      Temporarily changes the [Race Type](https://github.com/EQEmu/Server/wiki/Race-Types) of the client character that triggered the event to the specified race.

      **Example:**

```text
#:: Change race to Human
quest::playerrace(1);
```

### playersize

      **Parameter\(s\):**

      newsize _\(int\)_

      **Usage:**

      Temporarily adjusts the size of the client character that triggered the event to the specified size.

      **Example:**

```text
#:: Change size to 10
quest::playersize(10);
```

### playertexture

      **Parameter\(s\):**

      texture\_id _\(int\)_

      **Usage:**

      Temporarily changes the texture of the client character that triggered the event to the specified texture.

      **Example:**

```text
#:: Change texture to 2
quest::playertexture(2);
```

### popup

      **Parameter\(s\):**

      window\_title _\(string\)_, message _\(string\)_, popup\_id _\(int\)_, buttons _\(int\)_, duration _\(int\)_

      **Usage:**

      Used to create a popup window with the specified parameters. The parameters popup\_id, buttons, and duration are optional. Button parameters are: 0=OK button, 1=Yes/No buttons. Setting duration to 0 results in a popup that will remain until dismissed.

      **Example:**

```text
sub EVENT_ENTER {
     #:: Popup window entitled "Teleport", Question: "Teleport to The Plane of Hate?", popup ID 666, Yes/No buttons, remain until dismissed
     quest::popup('Teleport', 'Teleport to The Plane of Hate?', 666, 1, 0);
}

sub EVENT_POPUPRESPONSE {
     if ($popupid == 666) {
          #:: Teleport the player to The Plane of Hate
          quest::movepc(186,-393,656,3);
     }
}
```

### pvp

      **Parameter\(s\):**

      mode _\(string\)_

      **Usage:**

      Toggles the PVP setting for the client character that triggered the event. String can be on, or off.

      **Example:**

```text
#:: Turn pvp on
quest::pvp("on");
#:: Turn pvp off
quest::pvp("off");
```

### qs\_player\_event

      **Parameter\(s\):**

      character\_id _\(int\)_, message _\(string\)_

      **Usage:**

      Adds a record to table `qs_player_events` with the specified parameters.

      **Example:**

```text
quest::qs_player_event($charid,"Triggered an event with this API call in it.")
```

### qs\_send\_query

      **Parameter\(s\):**

      query _\(string\)_

      **Usage:**

      Send a raw query to the QueryServ process.

      **Example:**

```text
quest::qs_send_query("SELECT * FROM `qs_player_events` WHERE `event_desc` LIKE '%level%' LIMIT 0,1000;");
```

### rain

      **Parameter\(s\):**

      weather _\(int\)_

      **Usage:**

      Changes the rainy weather to the specified setting: 0=none, 1=rain. See also quest::snow\(\).

      **Example:**

```text
sub EVENT_ZONE {
     if ($name=~/turmoiltoad/i) {
          #:: Turn on the rain for those left behind
          quest::rain(1);
     }
}
```

### rebind

      **Parameter\(s\):**

      zone\_id _\(int\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_

      **Usage:**

      Binds the client character that triggered the event to the specified zone \(by Zone ID\) at the specified location.

      **Example:**

```text
#:: Change bind point to Rivervale, X=0, Y=0, Z=3.13
quest::rebind(19, 0.00, 0.00, 3.13);
```

### removetitle

      **Parameter\(s\):**

      title\_set\_id _\(int\)_

      **Usage:**

      Removes the specified Title Set from the client character that triggered the event.

      **Example:**

```text
#:: Remove Title Set 2 (prefix "Arbiter", suffix "Harbinger of the Old World")
quest::removetitle(2);
```

### repopzone

      **Parameter\(s\):**

      None.

      **Usage:**

      Repops the zone and re-enables spawn timers.

      **Example:**

```text
#:: Repop the zone
quest::repopzone();
```

### resettaskactivity

      **Parameter\(s\):**

      task\_id _\(int\)_, activity\_id _\(int\)_

      **Usage:**

      Sets the done count to 0 for the specified Task ID

      **Example:**

```text
#:: Reset the activity done count for task 202
quest::resettaskactivity(202);
```

### respawn

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_, grid\_id _\(int\)_

      **Usage:**

      Respawns the specified NPC by npc\_type ID on the specified grid. This is similar to quest::spawn2\(\), but without the specified x, y, z, heading parameters.

      **Example:**

```text
#:: Spawn Fippy Darkpaw again
quest::respawn(2001);
```

### resume

      **Parameter\(s\):**

      None.

      **Usage:**

      Used to resume pathing on a grid that has been stopped.

      **Example:**

```text
#:: Resume pathing on grid
quest::resume();
```

### safemove

      **Parameter\(s\):**

      None.

      **Usage:**

      Moves the client character that triggered the event to the safe coordinates of the current zone.

      **Example:**

```text
#:: Move to safe
quest::safemove();
```

### save

      **Parameter\(s\):**

      None.

      **Usage:**

      Saves the character data for the client character that triggered the event.

      **Example:**

```text
#:: Save Save Save
quest::save();
```

### say

      **Parameter\(s\):**

      message _\(string\)_, language\_id _\(int\)_

      **Usage:**

      Used to make your NPC speak.  [Language](https://github.com/EQEmu/Server/wiki/Languages) ID is optional--if not specified, the NPC will speak in common tongue.

      **Example:**

```text
quest::say("Hello.");
#:: Now in Barbarian
quest::say("Hello.", 1);
```

### saylink

      **Parameter\(s\):**

      message _\(string\)_, silent _\(bool\)_

      **Usage:**

      Used to create a say link. The silent parameter bools false by default, and is optional.

      **Example:**

```text
quest::say("This is [" . quest::saylink("purple text") . "] that you can click.");
```

### scribespells

      **Parameter\(s\):**

      max\_level _\(int\)_, min\_level _\(int\)_

      **Usage:**

      Used to add spells to the spell book of the client character that triggered the event.

      **Example:**

```text
#:: Scribe all spells up to current level
quest::scribespells($ulevel,1);
```

### selfcast

      **Parameter\(s\):**

      spell\_id _\(int\)_

      **Usage:**

      Used to cause client characters to cast the specified spell on themselves.

      **Example:**

```text
#:: Not with your hand, with MY hand!
quest::selfcast(521);
```

### set\_proximity

      **Parameter\(s\):**

      min\_x _\(float\)_, max\_x _\(float\)_, min\_y _\(float\)_, max\_y _\(float\)_, min\_z _\(float\)_, max\_z _\(float\)_, say _\(bool\)_

      **Usage:**

      Used to create a proximity around an NPC. Necessary to define for both EVENT\_ENTER and EVENT\_PROXIMITY\_SAY \(bool the say parameter to true to use this event\). Z min/max and enabling proximity say are both optional.

      **Example:**

```text
sub EVENT_SPAWN {
	#:: Create a proximity, 100 units across, 100 units tall, without proximity say
	quest::set_proximity($x - 50, $x + 50, $y - 50, $y + 50, $z - 50, $z + 50, 0);
}

sub EVENT_PROXIMITY_SAY {
	#:: Match say message for "hail", /i for case insensitive
	if ($text=~/hail/i) {
		quest::say("Hello, $name!");
	}
}

sub EVENT_ENTER {
	#:: Say "hello" when someone nears
	quest::say("Hello, $name!");
}
```

### set\_zone\_flag

      **Parameter\(s\):**

      zone\_id _\(uint32\)_

      **Usage:**

      Used to set a zone flag for the client character that triggered the event.

      **Example:**

```text
sub EVENT_SAY {
     if ($text=~/Darkness Beckons/i &&  defined $qglobals{pop_pon_construct} &&  defined $qglobals{pop_pon_hedge_jezith}) {
          $client->Message(1,"Very well mortal... you shall pass into the Lair of Terris Thule");
          $client->Message(2,"You now have access to the Lair of Terris Thule!");
          quest::set_zone_flag(221);
     }
}
```

### setallskill

      **Parameter\(s\):**

      value _\(int\)_

      **Usage:**

      Sets all [Skills](https://github.com/EQEmu/Server/wiki/Skills) to the specified value. You might want to consider a slightly more pinpoint approach like that found in the [Skill Maxer](https://github.com/EQEmu/Server/wiki/Buff-your-Players#Skill_Maxer_PERL) bot.

      **Example:**

```text
#:: Set every possible skill to 300--you probably shouldn't do this.
quest::setallskill(300);
```

### setanim

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_, appearance\_number _\(int\)_

      **Usage:**

      Used to make the NPC, specified by npc\_type ID, to do the specified animation. Parameters for the appearance are: 0=Stand, 1=Sit, 2=Duck, 3=Feign Death, 4=Kneel

      **Example:**

```text
#:: Make Fippy Darkpawn FD (he's going to die anyhow)
quest::(2001, 3);
```

### setglobal

      **Parameter\(s\):**

      key _\(string\)_, value _\(string\)_, options _\(int\)_, duration _\(string\)_

      **Usage:**

      Used to set a quest global.  **Consider using** [**Data Buckets**](https://github.com/EQEmu/Server/wiki/Data-Buckets) **instead.** Note that the name of the global is case sensitive.

| **Option** | **NPC ID** | **Player** | **Zone** |
| :--- | :--- | :--- | :--- |
| 0 | Current  | Current  | Current |
| 1 | All  | Current  | Current |
| 2 | Current  | All  | Current |
| 3 | All  | All  | Current |
| 4 | Current  | Current  | All |
| 5 | All  | Current  | All |
| 6 | Current  | All  | All |
| 7 | All  | All  | All |

| **Duration** | **Type** | **Example** |
| :--- | :--- | :--- |
| S | Seconds | S15 = 15 Seconds |
| M | Minutes | M30 = 30 Minutes |
| H | Hours   | H12 = 12 Hours |
| D | Days    | D90 = 90 Days |
| Y | Years   | Y5 = 5 Years |
| F | Forever | Never expires. |

      **Example:**

```text
#:: Set the qglobal "Example", to a value of "1", for all NPCs and zone, and last forever
quest::setglobal("Example", 1, 5, "F");
```

### setguild

      **Parameter\(s\):**

      guild\_id _\(int\)_, guild\_rank\_id _\(int\)_

      **Usage:**

      Sets the specified guild, by Guild ID, and the specified guild rank, by Rank ID, for the client character that triggered the event. Ranks are: 0=Member, 1=Officer, 2=Leader.

      **Example:**

```text
#:: Add to guild 24
quest::setguild(24,0);
```

### sethp

      **Parameter\(s\):**

      mob\_health\_percentage _\(int\)_

      **Usage:**

      Used to set the percentage \(0 to 100\) of health for the NPC.

      **Example:**

```text
#:: Restore HP to 50 percent
quest::sethp(50);
```

### setlanguage

      **Parameter\(s\):**

      skill\_id _\(int\)_, value _\(int\)_

      **Usage:**

      Used to set the specified [Language](https://github.com/EQEmu/Server/wiki/Languages) to the specified skill level \(0 to 100\).

      **Example:**

```text
sub EVENT_ENTERZONE {
	#:: Set common tongue to 1 for any new player that is not human
	if ($race ne "Human") {
		if (!defined $qglobals{"newbiecommon"}) {
			$client->SetLanguageSkill(0, 1);
			quest::setglobal("newbiecommon", 1, 5, "F");
		}
	}
}
```

### setnexthpevent

      **Parameter\(s\):**

      at\_mob\_percentage _\(int\)_

      **Usage:**

      Used to set an HP event \(to trigger EVENT\_HP\). When the NPC's health decreases to reach this threshold, the event will be triggered.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Trigger EVENT_HP at 90 percent
     quest::setnexthpevent(90);
}

sub EVENT_HP {
     #:: Match if HP is 90 percent
     if ($hpevent == 90) {
          quest::shout("My hit points have reached 90 percent!");
          #:: Trigger EVENT_HP at 80 percent
          quest::setnexthpevent(80);
     }
     elsif ($hpevent == 80) {
          quest::shout("My hit points have reached 80 percent!");
     }
}
```

### setnextinchpevent

      **Parameter\(s\):**

      at\_mob\_percentage _\(int\)_

      **Usage:**

      Used to set an HP event \(to trigger EVENT\_HP\). When the NPC's health increases to reach this threshold, the event will be triggered.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Trigger EVENT_HP at 90 percent
     quest::setnexthpevent(90);
}

sub EVENT_HP {
     #:: Match if hit points decrease to 90 percent
     if ($hpevent == 90) {
          quest::shout("My hit points have reached 90 percent--you better keep trying!");
          #:: Trigger EVENT_HP at 91 percent
          quest::setnextinchpevent(91);
     }
     #:: Match if hit points increase to 91 percent
     if ($inchpevent == 91) {
          quest::shout("You are no match for my power!");
          quest::sethp(100);
     }
}
```

### set\_rule

      **Parameter\(s\):**

      rule\_name _\(string\)_, rule\_value _\(string\)_

      **Usage:**

      Used to set the specified [Rule](https://github.com/EQEmu/Server/wiki/Server-Rules) to the specified value.

      **Example:**

```text
#:: Set Character:MaxLevel to 100 for the current zone.
quest::set_rule("Character:MaxLevel", 100);
```

### setskill

      **Parameter\(s\):**

      skill\_id _\(int\)_, value _\(int\)_

      **Usage:**

      Used to set the specified [Skill](https://github.com/EQEmu/Server/wiki/Skills) to the specified value.

      **Example:**

```text
#:: Set baking to 100
quest::setskill(60, 100);
```

### setsky

      **Parameter\(s\):**

      sky _\(uint8\)_

      **Usage:**

      Sets the parameter for the sky \(0 to 255\)

      **Example:**

```text
#:: Turn the sky red
quest::setsky(250);
```

### setstat

      **Parameter\(s\):**

      stat\_id _\(int\)_, value _\(int\)_

      **Usage:**

      Sets the specified stat to the specified value \(0 to 252\). Stats are: STR=0, STA=1, AGI=2, DEX=3, INT=4; WIS=5, CHA=6.

      **Example:**

```text
#:: Set STR to 250
quest::setstat(0, 250);
```

### settarget

      **Parameter\(s\):**

      target\_enum _\(string\)_, target\_id _\(int\)_

      **Usage:**

      Sets the target, by Target ID, for the specified target\_enum \(either npc\_type ID or entity ID\).

      **Example:**

```text
sub EVENT_SPAWN {
     my @clist = $entity_list->GetClientList();
     foreach my $c (@clist) {
          #:: Tell Fippy to kill!
          quest::settarget(2001, $c);
     }
}
```

### settime

      **Parameter\(s\):**

      new\_hour _\(int\)_, new\_min _\(int\)_, update\_world _\(bool\)_

      **Usage:**

      Sets the time for the zone or the world to the specified hour and minute. Update world is optional, but defaults to true--setting it to false makes the time change only apply to the current zone.

      **Example:**

```text
#:: Make it 5 o'clock somewhere
quest::settime(17,0);
#:: No--make it 5 o'clock everywhere!
quest::settime(17);
```

### settimer

      **Parameter\(s\):**

      timer\_name _\(string\)_, seconds _\(int\)_

      **Usage:**

      Sets a timer \(in seconds\) that will loop until you stop it. Gets caught by EVENT\_TIMER.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Set a timer that loops every 300 seconds (5 min)
     quest::settimer("despawn", 300);
}

sub EVENT_TIMER {
     if ($timer eq "despawn") {
          #:: Stop the timer from looping over and over
          quest::stoptimer("despawn");
          #:: Depop
          quest::depop();
     }
}
```

### settimerMS

      **Parameter\(s\):**

      timer\_name _\(string\)_, milliseconds _\(int\)_

      **Usage:**

      Sets a timer \(in milliseconds\) that will loop until you stop it. Gets caught by EVENT\_TIMER. Note that the Lua timer function is in milliseconds as well.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Set a timer that loops every 300000 milliseconds (5 min)
     quest::settimerMS("despawn", 300000);
}

sub EVENT_TIMER {
     if ($timer eq "despawn") {
          #:: Stop the timer from looping over and over
          quest::stoptimer("despawn");
          #:: Depop
          quest::depop();
     }
}
```

### sfollow

      **Parameter\(s\):**

      None.

      **Usage:**

      Used to stop quest::follow\(\);.

      **Example:**

```text
#:: Stop following
quest::sfollow();
```

### shout

      **Parameter\(s\):**

      message _\(string\)_

      **Usage:**

      Makes the NPC shout a message to the zone.

      **Example:**

```text
quest::shout("Let it all out!");
```

### shout2

      **Parameter\(s\):**

      message _\(string\)_

      **Usage:**

      Makes the NPC shout a message to the world.

      **Example:**

```text
quest::shout2("Let it all out!");
```

### showgrid

      **Parameter\(s\):**

      grid\_id _\(int\)_

      **Usage:**

      Displays the pathing grid specified by Grid ID.

      **Example:**

```text
#:: Show grid 20
quest::showgrid(20);
```

### signal

      **Parameter\(s\):**

      npc\_id _\(int\)_, wait\_ms _\(int\)_

      **Usage:**

      Sends a signal to an NPC, specified by NPC ID, after a wait period of the specified milliseconds. Wait is optional and defaults to 0ms. Compare to quest::signalwith\(\). Signals trigger EVENT\_SIGNAL.

      **Example:**

```text
sub EVENT_SAY {
	#:: If faction is indifferent or better
	if ($faction < 4) {
		if ($text=~/hail/i) {
			quest::say("Greetings, my friend! You may rest here if you like. There are many dangers in this land. May Tunare watch over you when you depart our camp.");
			#:: signal 70005 - Elmion Hendrys after a 5ms pause
			quest::signal(70005,5);
		}
	} 
	else {
		quest::say("You have some nerve to approach a loyal member of the Paladins of Tunare! Run, while you can!");
	}
}
```

### signalwith

      **Parameter\(s\):**

      npc\_id _\(int\)_, signal\_id _\(int\)_, wait\_ms _\(int\)_

      **Usage:**

      Sends a signal to an NPC, specified by NPC ID, with a specified Signal ID, after a wait period of the specified milliseconds. Wait is optional and defaults to 0ms. Compare to quest::signal\(\). Signals trigger EVENT\_SIGNAL.

      **Example:**

```text
sub EVENT_WAYPOINT_ARRIVE {
	if ($wp==12) {
		#:: Send a signal "2" to Steamfont Mountains >> Charlotte (56108), after 1ms
		quest::signalwith(56108,2,1);
	}
	if ($wp==18) {
		#:: Send a signal "3" to Steamfont Mountains >> Charlotte (56108), after 1ms
		quest::signalwith(56108,3,1);
	}
}
```

### snow

      **Parameter\(s\):**

      weather _\(int\)_

      **Usage:**

      Changes the snowy weather to the specified setting: 0=none, 1=snow. See also quest::rain\(\).

      **Example:**

```text
sub EVENT_ZONE {
     if ($name=~/turmoiltoad/i) {
          #:: Turn on the snow for those left behind
          quest::snow(1);
     }
}
```

### spawn

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_, grid\_id _\(int\)_, int\_unused _\(int\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_

      **Usage:**

      Spawns an NPC by NPC Type ID, on the specified grid, by Grid ID. The unused int corresponds to guildwarset--use 0 for this value as it is presently unused.

      **Example:**

```text
#:: Spawn Fippy_Darkpaw (2001) on grid 103 at the specified location
quest::spawn(2001, 103, 0, 481.20, 1210.80, 3.10);
```

### spawn2

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_, grid\_id _\(int\)_, int\_unused _\(int\)_, x _\(float\)_, y _\(float\)_, z _\(float\)_, heading _\(float\)_

      **Usage:**

      Spawns an NPC by NPC Type ID, on the specified grid, by Grid ID. The unused int corresponds to guildwarset--use 0 for this value as it is presently unused. Similar to quest::spawn\(\), with the addition of a heading parameter.

      **Example:**

```text
#:: Spawn Fippy_Darkpaw (2001) on grid 103 at the specified location, facing East
quest::spawn2(2001, 103, 0, 481.20, 1210.80, 3.10, 90);
```

### spawn\_condition

      **Parameter\(s\):**

      zone\_short _\(string\)_, instance\_id _\(int\)_, condition\_id _\(uint16\)_, value _\(int16\)_

      **Usage:**

      Sets the condition and value for the zone spawn condition. Instance ID is optional and defaults to 0. You might use this to stop certain NPCs from spawning during a raid event.

      **Example:**

```text
sub EVENT_SPAWN {
	#:: Set the condition to 3 value 0 to stop a_doomfire_chaosfiend spawn points
	quest::spawn_condition($zonesn, $instanceversion, 3, 0);
}
```

### spawn\_from\_spawn2

      **Parameter\(s\):**

      spawn2\_id _\(int\)_

      **Usage:**

      Used to force a spawn\_2 point to spawn an NPC even if disabled, or if it already has an NPC spawned.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Create a timer that loops every 10 seconds called "fippy")
     quest::settimer("fippy", 10);
}

sub EVENT_TIMER {
     #:: Match timer "fippy"
     if ($timer eq "fippy") {
          #:: Spawn ANOTHER Fippy, which will create another timer, spawn ANOTHER Fippy...chaos ensues.
          quest::spawn_from_spawn2(10875);
     }
}
```

### start

      **Parameter\(s\):**

      grid\_id _\(int\)_

      **Usage:**

      Used to start an NPC on the specified pathing grid.

      **Example:**

```text
sub EVENT_SIGNAL {
	#:: Match if signal from steamfont/Jogl_Doobraugh.pl is "1"
	if (($signal == 1) && (($x == -495) || ($x == -734)) && (($y == -154) || ($y == 114))) {
		quest::emote("Beep.. Beep.. Beep..");
		quest::pause(60);
	}
	#:: Match if signal from steamfont/Jogl_Doobraugh.pl is "2"
	if ($signal == 2) {
		#:: Start path grid 178
		quest::start(178);
	}
	#:: Match if signal from steamfont/Jogl_Doobraugh.pl is "3"
	if ($signal == 3) {
		#:: Start path grid 179
		quest::start(179);
	}
}
```

### stop

      **Parameter\(s\):**

      None.

      **Usage:**

      Used to stop an NPC.

      **Example:**

```text
sub EVENT_TIMER {
	#:: Match "CargoTimer" every five seconds
	if ($timer eq "CargoTimer") {
		#:: Match if the quest was not a failure and the time is 8 AM
		if (!defined($qglobals{CargoClockwork}) && ($zonehour == 8)) {
			#:: Set a qglobal in case of quest failure
			quest::setglobal("CargoClockwork",1,1,"H2");
			#:: Start path grid 177 - path to the windmills
			quest::start(177);
		}
		#:: Match if at the spawnpoint (WP 0) and if delivery was completed
		if ($x == 700 && $y == -1783 && $delivery == 1) {
			#:: Stop pathing on path grid 177
			quest::stop();
			#:: Reset the delivery state
			$delivery = 0;
		}
	}
}
```

### stopalltimers

      **Parameter\(s\):**

      None.

      **Usage:**

      Stops all the timers currently running from the script.

      **Example:**

```text
#:: Stop all the timers
quest::stopalltimers();
```

### stoptimer

      **Parameter\(s\):**

      timer\_name _\(string\)_

      **Usage:**

      Stops the specified timer from looping.

      **Example:**

```text
sub EVENT_SPAWN {
     #:: Set a timer "despawn" to loop every 300 seconds (5 min)
     quest::settimer("despawn", 300);
}

sub EVENT_TIMER {
     #:: Stop the timer "despawn"
     quest::stoptimer("despawn");
     #:: Depop
     quest::depop();
}

sub EVENT_COMBAT {
     #:: Stop the timer if we enter combat
     if ($combat_state == 1) {
          quest::stoptimer("despawn");
     }
     #:: Start the timer once combat is finished
     else {
          quest::settimer("despawn", 300);
     }
}

sub EVENT_DEATH_COMPLETE {
     #:: Stop the timer "despawn" if I die
     quest::stoptimer("despawn");
}
```

### summonallplayercorpses

      **Parameter\(s\):**

      char\_id _\(int\)_, dest\_x _\(float\)_, dest\_y _\(float\)_, dest\_z _\(float\)_, dest\_heading _\(float\)_

      **Usage:**

      Summons all character corpses, by Char ID, to the specified location.

      **Example:**

```text
sub EVENT_SAY {
     if ($text=~/corpses/i) {
          quest::say("Summoning all of your corpses now.");
          #:: Summon all player corpses to the current location, facing North
          quest::summonallplayercorpses($charid, $x, $y, $z, 0);
     }
}
```

### summonburiedplayercorpse

      **Parameter\(s\):**

      char\_id _\(uint32\)_, dest\_x _\(float\)_, dest\_y _\(float\)_, dest\_z _\(float\)_, dest\_heading _\(float\)_

      **Usage:**

      Summons all buried character corpses, by Char ID, to the specified location.

      **Example:**

```text
sub EVENT_SAY {
     $corpse = quest::getplayerburiedcorpsecount($charid);
     if ($text=~/corpses/i && $corpse > 0) {
          #:: Summon all buried player corpses to the current location, facing North
          quest::summonburiedplayercorpse($charid, $x, $y, $z, 0);
     }
}
```

### summonitem

      **Parameter\(s\):**

      item\_id _\(int\)_, charges _\(int\)_

      **Usage:**

      Summons the specified item, by Item ID, with the specified number of charges, to the cursor of the client character that triggered the event. Charges is the number of charges, or the count of the item, and is optional.

      **Example:**

```text
sub EVENT_ITEM {
	#:: Match 66gp and a 13990 - Bale of Hay
	if (plugin::takeItemsCoin(0,0,66,0, 13990 => 1)) {
		quest::say("'Whatsssss thisssss? You sssseek my blessssssssing? Heh heh heh... Very well... CAZIC-THULE! Take this fruit of Karana into horror'sss dark embrace. Fear and death made manifesssssst. A harvesssst of terror! Here, take your gift of blood and sssstraw. Use its dark powersssss in the name of the Fear Lord!' ");
		#:: Give a 14320 - Sack of Cursed Hay
		quest::summonitem(14320);
		#:: Ding!
		quest::ding();
		#:: Give a small amount of experience
		quest::exp(300);
		#:: Set faction
		quest::faction(18, 10);		#:: + Beta Neutral
	}
	#:: Return unused items
	plugin::returnUnusedItems();
}
```

### surname

      **Parameter\(s\):**

      name _\(string\)_

      **Usage:**

      Changes the surname of the client character that triggered the event to the provided string.

      **Example:**

```text
#:: Set last name to "Toad"
quest::surname("Toad");
```

### targlobal

      **Parameter\(s\):**

      key _\(string\)_, value _\(string\)_, duration _\(string\)_, npc\_id _\(int\)_, chararacter\_id _\(int\)_, zone\_id _\(int\)_

      **Usage:**

      Sets a quest global with the given parameters to a character anywhere in the world.

      **Example:**

```text
#:: Set a global "Example" with a value of "5" for 30 minutes
quest::targlobal("Example", "5", "M30", 2001, $charid, $zoneid);
```

### task\_setselector

      **Parameter\(s\):**

      task\_set\_id _\(int\)_

      **Usage:**

      Sets the Task Set, by provided Task Set ID.

      **Example:**

```text
#:: Set task set 202
quest::task_setselector(202);
```

### taskexplorearea

      **Parameter\(s\):**

      explore\_id _\(int\)_

      **Usage:**

      Used to mark any explore activities \(type 5\), which have the numeric value Explore ID in their Goal ID field, and for which the Zone ID of the activity is either 0 or this zone, as completed.

      **Example:**

```text
#:: Mark Task 21 complete
quest::taskexplorearea(21);
```

### taskselector

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Used to bring up the Task Selector Window with the specified tasks available for selection \(from 1 to 40 task\_id\(s\)\). Note that when the task selector is brought up via this method, no check is made as to whether the character has the tasks enabled.

      **Example:**

```text
sub EVENT_SAY {
     if ($text=~/hail/i) {
          quest::say("Heyo! Looking for an exciting [task] to fill the time?");
     }
     if ($text=~/task/i) {
          #:: Select task 103
          quest::taskselector(103);
     }
}
```

### tasktimeleft

      **Parameter\(s\):**

      task\_id _\(int\)_

      **Usage:**

      Returns the amount of time left, in seconds, before the specified task runs out. -1 is returned if there is no time limit, or if the player does not have the task.

      **Example:**

```text
#:: Create a scalar variable to store the amount of time left for Task ID 22
$timeremaining = quest::tasktimeleft(22);  #:: Returns int
if ($timeremaining => 1) {
     quest::say("You have $timeremaining seconds left--better hurry!");
}
else {
     quest::say("Sorry $name, but you're out of time!");
}
```

### toggle\_spawn\_event

      **Parameter\(s\):**

      event\_id _\(uint32\)_, is\_enabled _\(bool\)_, is\_strict _\(bool\)_, reset\_base _\(bool\)_

      **Usage:**

      Used to toggle the enabled state of a specified [Spawn Event](https://github.com/EQEmu/Server/wiki/spawn_events), by Event ID. The parameters for is\_enabled, is\_strict, and reset\_base are all false by default.

      **Example:**

```text
sub EVENT_DEATH_COMPLETE {
     #:: Turn the depop spawn_event back on
     quest::toggle_spawn_event(65, 1, 0, 0);
}
```

### toggledoorstate

      **Parameter\(s\):**

      door\_id _\(int\)_

      **Usage:**

      Toggles the open/closed state of the specified door.

      **Example:**

```text
sub EVENT_CLICKDOOR {
     my $tds = quest::isdooropen(41);
     my $bds = quest::isdooropen(42);
     if (($doorid == 41 && !$tds) || ($doorid == 42 && !$bds)) {
          quest::toggledoorstate(38);
          quest::toggledoorstate(39);
          quest::toggledoorstate(40);
     }
}
```

### traindisc

      **Parameter\(s\):**

      tome\_item\_id _\(int\)_

      **Usage:**

      Trains the discipline of the specified Tome ID for the client character that triggered the event. Generally you will simply use the plugin: plugin::try\_tome\_handins\(%itemcount, $class, 'Ranger'\);--part of the contents of which are in the example below.

      **Example:**

```text
if (@tomes > 0) {
	if ($isclass eq $expectclass) {
		foreach my $i(@tomes) {
			quest::traindisc($i);
		}
	}
}
```

### traindiscs

      **Parameter\(s\):**

      max\_level _\(int\)_, min\_level _\(int\)_

      **Usage:**

      Used to train all disciplines for the class up to the specified max\_level, if that level is less than rule Character:MaxLevel, or the character is a GM. The parameter for min\_level defaults to 1.

      **Example:**

```text
#:: Train disciplines up to level 70
quest::traindiscs(70,1);
```

### unique\_spawn

      **Parameter\(s\):**

      npc\_type\_id _\(int\)_, grid\_id _\(int\)_, int\_unused _\(int\)_, x _\(float\)_, y _\(float\)_, z\_ \(float\)\_, heading _\(float\)_

      **Usage:**

      Similar to the quest::spawn\(\) command, except that it will not spawn the specified NPC if the same npc\_type ID is already in the zone.

      **Example:**

```text
sub EVENT_DEATH_COMPLETE {
	my $random_result = int(rand(100));
	if ($random_result >= 94) {
		#:: Spawn a Steamfont Mountains >> Minotaur_Hero (56152)
		quest::unique_spawn(56152,177,0,-1294,1360,-103);
	}
	elsif ($random_result >= 88 && $random_result < 94) {
		#:: Spawn a Steamfont Mountains >> Minotaur_Lord (56161)
		quest::unique_spawn(56161,0,0,-2179,1319,-101.2);
	}
	quest::say("I die soon! Meldrath, help me!");
}
```

### unscribespells

      **Parameter\(s\):**

      None.

      **Usage:**

      Unscribes all spells for the client character that triggered the event.

      **Example:**

```text
#:: Unscribe all spells
quest::unscribespells();
```

### untraindiscs

      **Parameter\(s\):**

      None.

      **Usage:**

      Untrains all disciplines for the client character that triggered the event.

      **Example:**

```text
#:: Untrain all disciplines
quest::untraindiscs();
```

### updatetaskactivity

      **Parameter\(s\):**

      task\_id _\(int\)_, activity\_id _\(int\)_, count _\(int\)_, ignore\_quest\_update _\(bool\)_

      **Usage:**

      Used to increment the done count of the specified task is active. The parameter for ignore\_quest\_update is optional, and defaults to false; the parameter for count default to 1 \(increase count by 1\).

      **Example:**

```text
#:: Update Task ID 219 activity 9, by 1 count
quest::updatetaskactivity(216,9);
```

### varlink

      **Parameter\(s\):**

      item\_id _\(uint32\)_

      **Usage:**

      Used to create an item link that can be used in a variable.

      **Example:**

```text
#:: Create a scalar variable to store an item link for a 1001 - Cloth Cap
my $Reward = quest::varlink(1001);
```

### voicetell

      **Parameter\(s\):**

      client\_name _\(string\)_, macro\_id _\(int\)_, race\_id _\(int\)_, gender\_id _\(int\)_

      **Usage:**

      Plays the specified audio message on the client of the character that triggered the event.

      **Example:**

```text
#:: Send voice macro "Agree" to the client
quest::voicetell($name, 1);
```

### we

      **Parameter\(s\):**

      emote\_color\_id _\(int\)_, message _\(string\)_

      **Usage:**

      Sends an emote message to the world in the specified color.

      **Example:**

```text
#:: Send yellow (15) text
quest::we(15, "Hello world!");
```

### wearchange

      **Parameter\(s\):**

      slot _\(uint8\)_, texture\_id _\(uint16\)_, hero\_forge\_model\_id _\(uint32\)_, elite\_material\_id _\(uint32\)_

      **Usage:**

      Used to change the texture/model of visible [Slots](https://github.com/EQEmu/Server/wiki/Inventory-Slots). The parameters for hero\_forge\_model and elite\_material\_id default to 0.

      **Example:**

```text
#:: Change the appearance of the character's weapon
quest::wearchange(13, 3);
```

### worldwidemarquee

      **Parameter\(s\):**

      color\_id _\(uint32\)_, priority _\(uint32\)_, fade\_in _\(uint32\)_, fade\_out _\(uint32\)_, duration _\(uint32\)_, message _\(string\)_

      **Usage:**

      Used to send a worldwide marquee message with the specified parameters.

      **Example:**

```text
#:: Send a worldwide marquee message in yellow (15), 
quest::worldwidemarquee(15, 1, 1, 1, 1000, "Hello World!");
```

### write

      **Parameter\(s\):**

      file\_name _\(string\)_, message _\(string\)_

      **Usage:**

      Writes the specified message string to the specified file name.

      **Example:**

```text
quest::write("HandIn/$npc_name$zonesn.txt","[$timestamp] : $name the $ulevel has handed in $Item1, $Item2, $Item3, $item4 into $npc_name, and gotten $RewardID.");
```

### ze

      **Parameter\(s\):**

      emote\_color\_id _\(int\)_, message _\(string\)_

      **Usage:**

      Sends a zone-wide emote message in the specified color.

      **Example:**

```text
#:: Send a zone-wide emote in yellow (15)
quest::ze(15,"welcomes the world.");
```

### zone

      **Parameter\(s\):**

      zone\_name _\(string\)_

      **Usage:**

      Sends the client character that triggered the event to the specified zone \(by zone short name\).

      **Example:**

```text
#:: Send the player to the West Commonlands
quest::zone(commons);
```

