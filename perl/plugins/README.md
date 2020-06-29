# Plugins

* **Plugins:** [**https://github.com/ProjectEQ/projecteqquests/tree/master/plugins**](https://github.com/ProjectEQ/projecteqquests/tree/master/plugins)\*\*\*\*
  * Perl plugins are ALWAYS installed to ServerDirectory\plugins\ NOT ServerDirectory\quests\plugins\

**Extensive Plugin Explanation Pages:**

* [DiaWind](diawind.md) - This plugin is an extensive plugin for quest::popup \(Popup window uses\) - Akkadius
* [Doors Manipulation](doors-manipluation.md) - This plugin is revolves around letting developers manipulate objects/doors in realtime to custom fit their story/servers vision. - Akkadius
* [Expeditions and Shared Tasks](expeditions-and-shared-tasks.md) - Akkadius
* [Diablo Loot](diablo-loot.md) - Akkadius

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>File</b>
      </th>
      <th style="text-align:left"><b>Plugin &amp; Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">anim.pl</td>
      <td style="text-align:left">
        <p><b>plugin::DoAnim(&quot;salute&quot;); </b>
        </p>
        <p><b>Description:</b> Will take in an easy to remember name or string and
          take care of the conversion to ID in the scripting process.</p>
        <p>See <a href="https://eqemu.gitbook.io/server/categories/reference-lists/animations">Animations Reference List</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">anim.pl</td>
      <td style="text-align:left">
        <p><b>plugin::SetAnim(&quot;animation&quot;) see below for SetAnim options (stand/sit/duck/dead/kneel)</b>
        </p>
        <p>
          <br /> <b>Description:</b> Will take in an easy to remember name or string and
          take care of the conversion to ID in the scripting process</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">check_hastitem.pl</td>
      <td style="text-align:left">
        <p><b>plugin::check_hasitem($client, itemid)</b>
        </p>
        <p>Checks for items in just about every place for a player</p>
        <ul>
          <li>#Checks to see if player has item</li>
          <li>#Check main inventory and cursor</li>
          <li>#Check main inventory&apos;s and cursor&apos;s containers</li>
          <li>#Check bank slots</li>
          <li>#Check bank&apos;s containers</li>
          <li>#Check shared bank</li>
          <li>#Check shared bank&apos;s containers</li>
          <li>#Check corpses</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">check_handin.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::check_handin</b>
          </li>
          <li><b>plugin::return_items</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">guildmasters.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::try_tome_handins</b>
            <ul>
              <li>looks through the items haded in for discipline tomes, processing them
                as we find them.</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">group_utility.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>@members = plugin::GetGroupMembers($client)</b>
          </li>
          <li><b>plugin::MoveGroup(zoneid, x, y, z, h)</b>
          </li>
          <li><b>plugin::MoveGroupInstance(zoneid, instanceid, x, y, z, h)</b>
          </li>
          <li><b>plugin::CastOnGroup(SpellID, MaxDist=0, Client=$client);</b>
          </li>
          <li><b>plugin::MessageGroup(color, message)</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">illusion_tools.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::RandomFeatures(Mob);</b>
          </li>
          <li><b>plugin::CloneAppearance(MobA, MobB, CloneName=false);</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Instances.pl</td>
      <td style="text-align:left">
        <p><b>plugin::SendToInstance(&quot;solo/guild/group/public&quot;, &quot;Zone Short Name&quot;, Version, X, Y, Z, &quot;Identifier&quot;, duration in seconds&quot;);</b>
        </p>
        <p><b>Description</b>
        </p>
        <p>Used to simplify the instancing process.</p>
        <p>Also keeps track of the Zone ID via qglobals, so whatever NPC you use
          this on must have qglobals enabled!</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">spawn_utils.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>my $LoSDistance = plugin::GetMaxLoSDistFromHeading(Heading, [DistIncrements, MaxDist, Mob]);</b>
          </li>
          <li><b>plugin::FaceBestHeading([MinLoSDist]);</b>
          </li>
          <li><b>my $ShortestHeading = plugin::HeadingToShortestLoS([MaxDistToCheck=8]);</b>
          </li>
          <li><b>my $NPCMoved = plugin::MoveAwayFromWall([MinLoSDist=5]);</b>
          </li>
          <li><b>plugin::MoveToFirstBestZ();</b>
          </li>
          <li><b>plugin::SpawnZone(X, Y, Z, Distance, Variance, Columns, Rows);</b>
          </li>
          <li><b>my $ReverseHeading = plugin::GetReverseHeading([$mob]);</b>
          </li>
          <li><b>my $Degrees = plugin::ConvertHeadingToDegrees(Heading);</b>
          </li>
        </ul>
        <p>This is used for populating zones from scratch</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">spawn_utils.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::moelib_spawn_block(npctypeid, fromx, tox, fromy, toy, space, zposition=20, heading=0, grid=0)</b>
            <ul>
              <li>Spawns NPC&apos;s in a block</li>
            </ul>
          </li>
          <li><b>plugin::moelib_spawn_block_center(npctypeid, centerx, centery, range, amount, zposition=20, heading=0, grid=0)</b>
            <ul>
              <li>Spawns NPC&apos;s in a block around specified &apos;center&apos; coordinate</li>
            </ul>
          </li>
          <li><b>plugin::moelib_spawn_circle(npctypeid, centerx, centery, radius, amount, zposition=20, heading=0, grid=0)</b>
            <ul>
              <li>Spawns NPC&apos;s in a circle</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">random_messages.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::RandomSay(chance(1-100), &quot;message1&quot;,&quot;message2&quot;, etc..);</b>
          </li>
          <li><b>plugin::RandomSay(chance(1-100), &quot;message1&quot;,&quot;message2&quot;, etc..);</b>
          </li>
          <li><b>plugin::RandomEmote(chance(1-100), &quot;message1&quot;,&quot;message2&quot;, etc..);</b>
          </li>
          <li><b>plugin::RandomGroupEmote(chance(1-100), &quot;message1&quot;,&quot;message2&quot;, etc..);</b>
          </li>
          <li><b>plugin::RandomCloseEmote(chance(1-100), &quot;message1&quot;,&quot;message2&quot;, etc..);</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">text_formatting.pl</td>
      <td style="text-align:left">
        <ul>
          <li>plugin::commify(12302302); Would output value 12,302,302</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">random_range</td>
      <td style="text-align:left">
        <ul>
          <li>plugin::RandomRange(minvalue, maxvalue);</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">mob_utils.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::MobHealPercentage(Percent [1-100]);</b>
          </li>
          <li><b>plugin::MobDamagePercentage(Percent [1-100]);</b>
          </li>
          <li><b>plugin::MobHealPoints(Number);</b>
          </li>
          <li><b>plugin::MobDamagePoints(Number);</b>
          </li>
          <li><b>plugin::SpawnInPlace(NPCID To Spawn In Place, [1 = Don&apos;t depop what spawns in place]);</b>
          </li>
          <li><b>plugin::SpawnInPlaceByEnt{(NPCID To Spawn In Place, [1 = Don&apos;t depop what spawns in place]);</b>
          </li>
          <li><b>plugin::SpawnChest{(NPCID To Spawn In Place, [1 = Don&apos;t depop what spawns in place]);</b>
            <ul>
              <li>This will spawn a chest within proximity with specified NPC ID</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">npc_tools.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::CountNPCTYPE($NPC_TYPE_ID);</b>
            <ul>
              <li>Description: Will return the number of NPC&apos;s in the zone from NPC
                ID</li>
            </ul>
          </li>
          <li><b>plugin::SetProx(X/Y Axis Range, Z Axis Range, [1 = Skeleton Reference proximity for debugging]);</b>
            <ul>
              <li>Description: This will set the proximity of an NPC, with simply two arguments,
                30 (x-y axis) and 30 (z axis)</li>
              <li>Note, if you set the 3rd arguement of SetProx to 1, it will spawn skeletons
                that represent how truly big your proximity is</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utility.pl</td>
      <td style="text-align:left"><b>plugin::AddLoot(amount, chance, @itemarray)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utility.pl</td>
      <td style="text-align:left">
        <p><b>plugin::SEV(entity, variable_name, variable_value)</b>
        </p>
        <p>This is a shorthand way of setting an entity variable.</p>
        <p>NOTE: Entity variables are EXTREMELY powerful! Know how to use them!</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utility.pl</td>
      <td style="text-align:left">
        <p><b>plugin::REV(entity, variable_name);</b>
        </p>
        <p>This is a shorthand way of reading an entity variable, it will return
          a value.</p>
        <p>NOTE: Entity variables are EXTREMELY powerful! Know how to use them!</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utility.pl</td>
      <td style="text-align:left">
        <p><b>plugin::CheckDist(entity, distance);</b>
        </p>
        <p>A simple way to return the distance between the NPC initiating this plugin
          and the player, useful for all kinds of situations. Will return true if
          within distance, false if not.If you are not familiar with entites, they
          can be a client, npc, object, door etc.You have to utilize entity_list
          calls to get an entity object</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">utility.pl</td>
      <td style="text-align:left">
        <p><b>plugin::CheckDistBetween2Ents(entity1, entity2, distance);</b>
        </p>
        <p>A simple way to return the distance between two select entities, useful
          for all kinds of situations. Will return true if within distance, false
          if not. If you are not familiar with entites, they can be a client, npc,
          object, door etc.You have to utilize entity_list calls to get an entity
          object</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">client_messages.pl</td>
      <td style="text-align:left">
        <p><b>plugin::Autovtell(&quot;voicemessage&quot;);</b>
        </p>
        <p><b>Options: </b>
        </p>
        <ul>
          <li>greet</li>
          <li>battle</li>
          <li>disagree</li>
          <li>follow</li>
          <li>greet</li>
          <li>heal</li>
          <li>help</li>
          <li>laugh</li>
          <li>part</li>
          <li>retreat</li>
          <li>stop</li>
          <li>thanks</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">client_messages.pl</td>
      <td style="text-align:left">
        <p><b>plugin::Whisper(&quot;Message&quot;);</b>
        </p>
        <p>Whispers a message to the player</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">client_messages.pl</td>
      <td style="text-align:left">
        <p><b>plugin::ClientSay(&quot;Message&quot;, &quot;Message2&quot;, &quot;Message3&quot;); </b>
        </p>
        <p>If Multiple arguments are supplied, it will return a random message from
          the list.
          <br />If any of the arguments is a number, it will parse that number as the
          color to use for the TextColor of the message</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">client_messages.pl</td>
      <td style="text-align:left">
        <p><b>plugin::MM(&quot;Message&quot;)</b>
        </p>
        <p>Will display a Marquee message on the screen</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DiaWind.pl</td>
      <td style="text-align:left">
        <p><b>plugin::DiaWind(&quot;Window text&quot;);</b>
        </p>
        <p>Plugin for making use of popup windows</p>
        <p><b>See </b><a href="diawind.md"><b>DiaWind</b></a>&lt;b&gt;&lt;/b&gt;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Doors_Manip.pl</td>
      <td style="text-align:left">This is a hooked mod, to see how to install and use. See Doors Manipulation</td>
    </tr>
    <tr>
      <td style="text-align:left">MP3.pl</td>
      <td style="text-align:left">
        <p><b>plugin::U_MP3</b>
        </p>
        <p>This plugin utilizes a database full of the EverQuest sound files and
          their lengths to utilize sound looping and other features.</p>
        <p>This is an extension of $client-&gt;PlayMP3 which can play both mp3/wav
          as well as the old EverQuest .xmi file format (MIDI)</p>
        <p>PlayMP3 packet will ignore the clients music and sound level sliders so
          this can be annoying if you use it, however this restores the ability to
          use music in EverQuest because this plugin will only play one sound file
          per IP, which allows music to be played without walking over each clients
          sound files.</p>
        <p>All of the sound file lengths are queried from the custom table listed
          below. All Wav/MP3 files are in this database, no XMI&apos;s. If you want
          to use XMI&apos;s you will have to use them on your own accord.</p>
        <p><b>Options:</b>
        </p>
        <p><b>repeat_on_end</b> - Will repeat the sound file after the song plays</p>
        <p><b>delay_repeat</b> - How long the sound timer will wait before repeating</p>
        <p><b>interrupt</b> - This will interrupt another sound that is playing</p>
        <p><b>Required Database Table:</b>
        </p>
        <p><a href="http://wiki.eqemulator.org/l/wa/files/MP3_Plugin/cust_sound_files.rar">DOWNLOAD</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">constants.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::Skill(SkillID)</b>
            <ul>
              <li><a href="https://eqemu.gitbook.io/server/categories/reference-lists/skills">Skill Reference List</a>
              </li>
            </ul>
          </li>
          <li><b>plugin::Class(class_id)</b>
            <ul>
              <li><a href="https://eqemu.gitbook.io/server/categories/reference-lists/class-list">Class Reference List</a>
              </li>
            </ul>
          </li>
          <li><b>plugin::Race(Race_ID)</b>
            <ul>
              <li><a href="https://eqemu.gitbook.io/server/categories/reference-lists/race-list">Race Reference List</a>
              </li>
            </ul>
          </li>
          <li><b>plugin::Deity(Deity_Name);</b>
            <ul>
              <li><a href="https://eqemu.gitbook.io/server/categories/reference-lists/deity-list">Deity Reference List</a>
              </li>
            </ul>
          </li>
          <li><b>plugin::Gender(gender_id)</b>
            <ul>
              <li><a href="https://eqemu.gitbook.io/server/categories/reference-lists/genders">Gender Reference List</a>
              </li>
            </ul>
          </li>
          <li><b>plugin::Zone(zone_id) Returns zone long name</b>
          </li>
          <li><b>plugin::ZoneShortName(zone_id) Returns zone short name</b>
          </li>
          <li><b>plugin::ZoneIDBySN(zoneshortname) Returns zone short name</b>
            <ul>
              <li>&lt;b&gt;&lt;/b&gt;<a href="https://eqemu.gitbook.io/server/categories/reference-lists/zones"><b>Zone Reference List</b></a>&lt;b&gt;&lt;/b&gt;</li>
            </ul>
          </li>
          <li><b>plugin::SlotName(slotid) Returns slot name</b>
          </li>
          <li><b>plugin::IP($client-&gt;GetIP()) Gets the clients human readable IP</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Task_Utils.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::AssignTask(UpdateType=[solo, group, raid], TaskID, [NPCID = 0] ($npc&gt;GetID());</b>
          </li>
          <li><b>plugin::FailTask(UpdateType=[solo, group, raid], TaskID);</b>
          </li>
          <li><b>plugin::UpdateTaskActivity(UpdateType [solo, group, raid], TaskID, ActivityID, Count);</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">formation_tools.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::FollowFormLeader([LeaderMob, OnGrid = 0, MoveToX = 0, MoveToY = 0, NoSpeedBuffs = false]);</b>
          </li>
          <li><b>plugin::MoveInFormation(NPCID, [$npc = 0, OnGrid = 0, MoveToX = 0, MoveToY = 0, NoSpeedBuffs = false]);</b>
          </li>
          <li><b>plugin::MoveToFormation(NPCID, LeaderMob, Distance, Columns, Rows, [LeadDist, MaxZDiff]);</b>
          </li>
          <li><b>plugin::RandomFormRoam(MaxVariance, MaxZVariance, LoSMobSize);</b>
          </li>
          <li><b>plugin::SpawnInFormation(NPCID, LeaderMob, Distance, Columns, Rows, [LeadDist, MaxZDiff]);</b>
          </li>
          <li><b>plugin::SpawnInFormationXY(NPCID, X, Y, Z, Distance, Columns, Rows, Heading, MaxZDiff);</b>
          </li>
          <li><b>plugin::SpawnMixedFormation(LeaderMob, Distance, Columns, Rows, LeadDist=Distance, MaxZDiff=15, NPCID, NPCID...);</b>
          </li>
          <li><b>plugin::FollowInFormation(NPCID, Mob, [MaxZDiff]);</b>
          </li>
          <li><b>plugin::SquadAttackTarget(SquadNPCID, TargetID);</b>
          </li>
          <li><b>plugin::SquadAttackSquad(Squad1NPCID, Squad2NPCID);</b>
          </li>
          <li><b>plugin::GetReverseHeading($mob)</b>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">weapon_tools.pl</td>
      <td style="text-align:left">
        <ul>
          <li><b>plugin::RandomWeapons(MinModelNum, MaxModelNum, MyChance, MinShieldNum, MaxShieldNum, NoDualWield?, IgnoreClass? );</b>
          </li>
          <li><b>plugin::SetWeapons(PrimaryModel, SecondaryModel, EnableRemoving? );</b>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

