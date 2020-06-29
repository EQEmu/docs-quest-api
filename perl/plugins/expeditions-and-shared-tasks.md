# Expeditions and Shared Tasks

## Description

* The expedition system that I have built is not typical to that of Live, but offers all of the wants/needs that Live had in regards to Expeditions and it gives you a lot more flexibility
* This system allows you to take a version of a zone, whether it be the regular zone or an completely custom version of a zone, and make an instance out of it
* This allows you to make dungeon oriented combat that can be repeatable and grinded just like all modern MMO's
* Allows you to put a lockout on content for a specified period of time if you wanted to use it for a raid

## **Warranty**

* Given the complex nature of this plugin, there may be issues or bugs that arise. I can fix issues given solid data on what is occuring. The good news is that I've given this code a really good spin and ironed out most issues that I've not already thought of ahead of time.
* This is as is - a wonderful free plugin I've given everyone with 150+ hours spent getting it to the point that it is at. 
* I plan to make feature expansions over time, but right now this is pretty packed as an initial release

## **Expedition Features:**

* **Task Synchronization** - Will sync task progress for all members in the task if you set it to
* **Enforces Level Requirements**
* **Enforces Player Count Requirements**
  * **Enforced minimum player requirement as well as maximum**
* **Supports as small as 1 player, to 80+ players**
* **Will not allow more than the specified players to travel to the instance**
* **Supports Task Lockouts** - If lockout is set - players can't do the instance for the specified time frame until the lockout is lifted

## **Expedition Commands \(Available to players\)**

* **\#expedition leave** - Leaves expedition
* **\#expedition destroy** - If you are leader - will destroy your expedition
  * When destroying expedition, it will force all members inside of the instance to be booted to the NPC or place the expedition was initiated
* **\#expedition memberlist** - Will get your expedition memberlist in window format
* **\#expedition groupinvite** - Will invite the group of the playername specified
* **\#expedition invite** - Will send an invite request to playername specified
* **\#expedition makeleader** - Makes specified player leader of expedition
* **\#expsay** - Will send a message to Expedition chat

## **Logic**

* When a leader goes offline, a new leader is automagically elected
* When player level requirements are enforced, an expedition can not be given
* When a player recieves a lockout for the instance identifier, they cannot get it again 
* When shared tasks are enabled, and a person within the expedition receives an update, everyone else is queued to see if their task stage matches theirs
  * When a person goes offline and comes back online, their task progress is synchronized \(Only when the expedition is active\)
  * When a person is zoning, when they enter zone their task progress is synchronized
* When a person is removed from an expedition, their task that is tied to the expedition will also be removed
* When a person is invited to an expedition, the task tied to the expedition will also be added
* All common calls made in Perl leverage the use of comma separated qglobals that contain a bunch of data. This is stored in memory and referenced super fast across zones for scalability
* When members are removed or added from an instance, other members are notified via **quest::crosszonemessageplayerbyname**
* The memberlist window will display time remaining on an expedition

## Activating this Plugin

* You need Perl DBI.
* You need Expeditions.pl from the [Github repository](https://github.com/ProjectEQ/projecteqquests/plugins)
* You will need to paste this code at the bottom of your global\_player.pl

{% tabs %}
{% tab title="Perl" %}
```perl
#####################################
#::: Expedition System - Include :::#
#####################################
 
sub ExpdHandler_EVENT_ENTERZONE{
    @AdvInfo = LoadExpeditionInfo();
    plugin::CheckForStaleInstances();
    SynchronizeSharedTasks(); #::: Expedition System
}
 
sub ExpdHandler_EVENT_DISCONNECT{
    $connect = plugin::LoadMysql();
    $connect2 = plugin::LoadMysql();
    @AdvInfo = LoadExpeditionInfo();
    my $newleader = "";
    if($AdvInfo[2] == 1){
        my $query2 = "UPDATE `cust_inst_players` SET `is_leader` = '0' WHERE `inst_id` = '" . $AdvInfo[0] . "' AND `player_name` = '" . $client->GetCleanName() . "';";
        my $query_handle2 = $connect2->prepare($query2); $query_handle2->execute();
        my $query2 = "SELECT `player_name` FROM `cust_inst_players` WHERE `inst_id` = '" . $AdvInfo[0] . "' ORDER BY `time_invited` LIMIT 1";
        my $query_handle2 = $connect2->prepare($query2); $query_handle2->execute();
        while (@row = $query_handle2->fetchrow_array()){
            my $query = "UPDATE `cust_inst_players` SET `is_leader` = '1' WHERE `player_name` = '" . $row[0] . "'";
            my $query_handle = $connect->prepare($query); $query_handle->execute();
            if($Debug) { $What = "#::: Elect new leader #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
            quest::crosszonesignalclientbyname($row[0], 607);
            $newleader = $row[0];
        }
        NotifyExpeditionMembers($AdvInfo[0], "Expedition Leader " . $client->GetCleanName() . " has gone offline, " . $newleader . " is now the new expedition leader");
    }
}
 
sub ExpdHandler_EVENT_SAY{
    if($text=~/#expsay/i){  if(!$AdvInfo[0] > 0){ @AdvInfo = LoadExpeditionInfo(); } $text=~ s/#expsay //g;
        if($AdvInfo[0] > 0){ $client->ExpeditionMessage($AdvInfo[0], $text); } else{ $client->Message(15, "You are not part of an active expedition"); }
    }
    if($text=~/Queue Instance/i){ $text =~ s/Queue Instance//g; plugin::DisplayInstanceQueue($text); }
    if($text=~/Destroy Instance/i){ $text =~ s/Destroy Instance//g; plugin::DestroyInstance($client->GetCleanName()); }
    if($text=~/#expedition destroy/i){ plugin::DestroyInstance($client->GetCleanName()); }
    if($text=~/#expedition/i){
        #$Debug = " ";
        @AdvInfo = LoadExpeditionInfo();
        if($AdvInfo[0]){ #::: Checks for membership
            my @arg = split(' ', $text); #::: Break out arguements
            if($arg[1] eq "remove"){
                if($arg[2] eq ""){ $client->Message(15, "#expedition remove <playername>"); }
                elsif($arg[2] ne ""){ ExpeditionProcessRemove($arg[2]); }
            }
            elsif($arg[1] eq "groupinvite"){
                if($arg[2] eq ""){ $client->Message(15, "#expedition groupinvite <playername>"); }
                elsif($arg[2] ne ""){ ExpeditionProcessGroupInvite($arg[2]); }
            }
            elsif($arg[1] eq "invite"){
                if($arg[2] eq ""){ $client->Message(15, "#expedition invite <playername>"); }
                elsif($arg[2] ne ""){ ExpeditionProcessInvite($arg[2]); }
            }
            elsif($arg[1] eq "tasksync"){
                $client->Message(15, "[Expedition] Performing Task sync");
                SynchronizeSharedTasks();
            }
            elsif($arg[1] eq "memberlist"){ ExpeditionMemberList($arg[1]); }
            elsif($arg[1] eq "makeleader"){ ExpeditionMakeLeader($arg[2]); }
            elsif($arg[1] eq "leave"){ ExpeditionLeave($arg[1]); }
            elsif($arg[1] ne ""){
                $client->Message(15, "That is not a valid expedition command");
            }
            else{
                $client->Message(15, "#expedition commands:");
                $client->Message(15, "--- leave - Leaves expedition");
                $client->Message(15, "--- destroy - If you are leader, will destroy your current expedition");
                $client->Message(15, "--- memberlist - Will get your expedition memberlist");
                $client->Message(15, "--- groupinvite <playername> - Search for a player of another group to invite");
                $client->Message(15, "--- invite <playername> - Search for a player to invite");
                $client->Message(15, "--- remove <playername> - Search for a group/raid member to remove");
                $client->Message(15, "--- makeleader <playername> - Will pass leadership to another expedition member");
                $client->Message(15, "--- tasksync - If for whatever reason your task progress is out of sync with other players in the expedition, use this");
                $client->Message(15, "#expsay - Will send a message to your Expedition");
            }
        }else{ $client->Message(15, "You are not the member of an expedition"); }
        return;
    }
}
 
sub ExpdHandler_EVENT_TASK_COMPLETE{
    @AdvInfo = LoadExpeditionInfo();
    if($task_id == $AdvInfo[3]){
        #$client->Message(15, "You have completed a task, and it's associated with your expedition");
        my @ExpdInfo = split(',', $qglobals{"ExpdSharedTask_" . $AdvInfo[6]});
        if($ExpdInfo[1] == 0){
            if($AdvInfo[18] eq $zonesn && $instanceid > 0 && $AdvInfo[19] == 1){ #::: He's most likely in the instance so lets kick them out
                quest::MovePCInstance($AdvInfo[12], $AdvInfo[14], $AdvInfo[15], $AdvInfo[16], $AdvInfo[17], 0);
            }
            quest::setglobal("ExpdSharedTask_" . $AdvInfo[6], $AdvInfo[3] . ",1", 7, "S" . ($AdvInfo[9] - time)); #::: StoreTaskID and completion bit
            ProcessLockouts($AdvInfo[0], $AdvInfo[11], $AdvInfo[4]);
            plugin::DestroyInstance($client->GetCleanName(), "force", 1);
        }
    }
}
 
sub ProcessLockouts{
    $connect = plugin::LoadMysql();
    $connect2 = plugin::LoadMysql();
    $ExpdID = $_[0];
    $query = "SELECT player_name FROM cust_inst_players WHERE `inst_id` = '". $ExpdID . "';";
        if($Debug) { $What = "#::: DisplayInstanceQueue #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
        $query_handle = $connect->prepare($query); $query_handle->execute();
        $n = 0; $Players = "";
    while (@row = $query_handle->fetchrow_array()){
        $query2 = "INSERT INTO `cust_ext_lockouts` (player, lockout_name, lockout_expire) VALUES (?, ?, ?);";
        $query_handle2 = $connect2->prepare($query2); $query_handle2->execute($row[0], $_[2], (time + $_[1]));
        $query2 = "INSERT INTO `cust_ext_hist_lockouts` (player, lockout_name, lockout_expire) VALUES (?, ?, ?);";
        $query_handle2 = $connect2->prepare($query2); $query_handle2->execute($row[0], $_[2], (time + $_[1]));
    }
    if($Debug){ $client->Message(15, time . " " . " " . $_[1] . " " . localtime($_[1])); }
    NotifyExpeditionMembers($_[0], "You now have a lockout for '". $_[2] . "' which will expire in " . plugin::GetTimeLeftAdv(time + $_[1]) . "");
}
 
sub ExpdHandler_EVENT_TASK_UPDATE{
    if($Debug){ $client->Message(15, "DEBUG: Triggered Update, $task_id $activity_id with donecount $donecount"); }
    @AdvInfo = LoadExpeditionInfo();
    if($AdvInfo[6] && $task_id == $AdvInfo[3]){
        if($AdvInfo[6] > 0){ #::: Added this to prevent checking of updates when a expedition doesn't even take place
            @TaskProg = GetTaskProgress($AdvInfo[6]);
            if($Debug){ $client->Message(15, "DEBUG: ADVINFO $AdvInfo[6] $TaskProg[0]"); }
            if(@TaskProg){
                if($Debug){ $client->Message(15, "DEBUG: Yes, we have passed the task progression check"); }
                if($TaskProg[$activity_id] < $donecount){
                    if($Debug){ $client->Message(15, "DEBUG: We're processing this section of task code"); }
                    if($Debug){ $client->Message(15, "Your Donecount is greater than what is stored, yours $donecount, stored ". $TaskProg[$activity_id]); }
                    $TaskProg[$activity_id] = $donecount;
                    my $NV = ""; foreach my $val (@TaskProg){ $NV .= "$val,"; } quest::setglobal("ExpdSharedTaskProg_" . $AdvInfo[6], substr ($NV, 0, -1), 7, "S" . ($AdvInfo[9] - time));
                    @TaskMembers = GetExpdMembers($AdvInfo[0]);
                    foreach my $val (@TaskMembers){
                        if($val != $client->CharacterID()){
                            if($Debug){ $client->Message(15, "Sending to member " . $val); }
                            quest::crosszonesignalclientbycharid($val, 605);
                            quest::crosszonesignalclientbycharid($val, $activity_id);
                        }
                    }
                }
                my @TDefs = GetTaskActivityDefs($AdvInfo[3], $AdvInfo[9]);
                if($TaskProg[$activity_id] == $TDefs[$activity_id]){
                    my $NV = "";
                    for($i = 0; $i <= $activity_id; $i++){
                        if($TaskProg[$i] > $TDefs[$o]){ $NV .= "$TaskProg[$i],"; }else{ $NV .= "$TDefs[$i],"; }
                    }
                    quest::setglobal("ExpdSharedTaskProg_" . $AdvInfo[6], substr ($NV, 0, -1), 7, "S" . ($AdvInfo[9] - time));
                }
            }
        }
    }
}
 
sub ExpdHandler_EVENT_SIGNAL{
    #::: Expedition Signalling
    # my $Debug = 1;
    if($status > 200 && $Debug == 1){ $client->Message(15, "Signal is " . $signal); }
    if($signal == 600){ #::: Assigned to Expedition
        ExpeditionMemberList($arg[1]);
        @AdvInfo = LoadExpeditionInfo();
        if($AdvInfo[3]){ quest::assigntask($AdvInfo[3]); }
        $client->Message(15, "You have been assigned to expedition '". $AdvInfo[4] . "'");
        return;
    }
    if($client->GetEntityVariable("QueueExeditionTaskDeletion") == 1){ $client->FailTask($signal); $client->SetEntityVariable("QueueExeditionTaskDeletion", 0); return; }
    if($signal == 601){ #::: Remove from Expedition
        @AdvInfo = LoadExpeditionInfo();
        $client->Message(15, "Your expedition has come to an end.");
        $client->SetEntityVariable("QueueExeditionTaskDeletion", 1);
        quest::popup("", "Your expedition has come to an end...", 0, 0, 1);
        @AdvInfo = LoadExpeditionInfo();
        if($AdvInfo[18] eq $zonesn && $instanceid > 0){ #::: He's most likely in the instance so lets kick them out
            quest::MovePCInstance($AdvInfo[12], $AdvInfo[14], $AdvInfo[15], $AdvInfo[16], $AdvInfo[17], 0);
        }
        $client->DelGlobal("ExpdInfo_" . $name); #::: Purge Expedition Cached info...
        #if($qglobals{"ExpdSharedTask_" . $AdvInfo[6]}){ $client->DelGlobal("ExpdSharedTask_" . $AdvInfo[6]);}
        #if($qglobals{"ExpdSharedTaskProg_" . $AdvInfo[6]}){ $client->DelGlobal("ExpdSharedTaskProg_" . $AdvInfo[6]);}
        return;
    }
    if($client->GetEntityVariable("QueueExeditionExpdID") == 1){ #::: Queue Invitation Window
        ExpeditionMemberList("", $signal);
        $client->SetEntityVariable("QueueExeditionExpdID", 0);
        $client->SetEntityVariable("ExpdIDInvite", $signal);
        return; #::: We don't need to process anything since we're using a timed loose signal
    }
    if($signal == 602){ #::: Player Invited to Expedition
        $client->Message(15, "Receiving Expedition invitation...");
        $client->SetEntityVariable("QueueExeditionExpdID", 1);
    }
    if($client->GetEntityVariable("FailTaskID") == 1){
        $client->FailTask($signal);
        quest::popup("", "Your expedition has come to an end...", 0, 0, 1);
        $client->SetEntityVariable("FailTaskID", 0);
        @AdvInfo = LoadExpeditionInfo();
        if($AdvInfo[18] eq $zonesn && $instanceid > 0){ #::: He's most likely in the instance so lets kick them out
            quest::MovePCInstance($AdvInfo[12], $AdvInfo[14], $AdvInfo[15], $AdvInfo[16], $AdvInfo[17], 0);
        }
        $client->DelGlobal("ExpdInfo_" . $name); #::: Purge Expedition Cached info...
    }
    if($signal == 604){ #::: Expedition Remove
        $client->Message(15, "You have been removed from the expedition");
        $client->SetEntityVariable("FailTaskID", 1);
    }
    if($client->GetEntityVariable("ExpdTaskUpdate") == 1){
        if($status > 200 && $Debug == 1){ $client->Message(15, " "); $client->Message(15, "Hitting update"); }
        @AdvInfo = LoadExpeditionInfo();
        @TaskProg = GetTaskProgress($AdvInfo[6]);
        my $RecUpd = $TaskProg[$signal];
        if($AdvInfo[3] > 0){
            if($status > 200 && $Debug == 1){ $client->Message(15, "TASK ASSOC IS " . $AdvInfo[3]); }
            if($Debug) { $client->Message(15, "Debug $AdvInfo[3] $signal");  }
            my $Prog = quest::gettaskactivitydonecount($AdvInfo[3], $signal);
            if($status > 200 && $Debug == 1){ $client->Message(15, "PROG IS " . $Prog); }
            if($RecUpd > $Prog){
                if($status > 200 && $Debug == 1){ $client->Message(15, "REC UPDATE IS  " . $RecUpd); }
                if($Debug) { $client->Message(15, "Debug Stored progress is greater than mine, lets catch up"); }
                if($Debug) { $client->Message(15, "Debug UPDATE " . $AdvInfo[3] . ", " . $signal . " " . ($RecUpd - $Prog) . ""); }
                quest::updatetaskactivity($AdvInfo[3], $signal, ($RecUpd - $Prog));
            }
        }
        $client->SetEntityVariable("ExpdTaskUpdate", -1);
    }
    if($signal == 605){ #::: Task Update
        $client->SetEntityVariable("ExpdTaskUpdate", 1);
    }
    if($signal == 606){ #::: You've been re-elected leader, reset your shit
        @AdvInfo = LoadExpeditionInfo(1);
        NotifyExpeditionMembers($AdvInfo[0], $client->GetCleanName() . " has been elected as the new leader");
        return;
    }
    if($signal == 607){ #::: You were made leader, refresh your info
        @AdvInfo = LoadExpeditionInfo(1);
        return;
    }
    if($signal == 608){ #::: Task/Expedition complete! Let's wrap this up :)
        @AdvInfo = LoadExpeditionInfo();
        $client->Message(15, "Your expedition has been a complete success!");
        #::: Let's Make sure we truly are caught up task progress wise...
        my @TDefs = GetTaskActivityDefs($AdvInfo[3], $AdvInfo[9]);
        $n = 0;
        foreach my $val (@TDefs){ quest::updatetaskactivity($AdvInfo[3], $n, $val); $n++; }
        quest::doanim(27);
        quest::popup("", "Your expedition has come to an end...", 0, 0, 1);
        $client->DelGlobal("ExpdInfo_" . $name); #::: Purge Expedition Cached info...
        if($qglobals{"ExpdSharedTask_" . $AdvInfo[6]}){ $client->DelGlobal("ExpdSharedTask_" . $AdvInfo[6]);}
        if($qglobals{"ExpdSharedTaskProg_" . $AdvInfo[6]}){ $client->DelGlobal("ExpdSharedTaskProg_" . $AdvInfo[6]);}
        return;
    }
    #::: END Expedition Signalling
     
}
 
sub ExpdHandler_EVENT_POPUPRESPONSE{
    if($popupid == 600){ #::: Accept Expedition Creation
        #::: InitInstance Variables are recalled here - 2nd passing
        for($i=0;$i<=19;$i++){ $E[$i] = $client->GetEntityVariable("InstRequest" . $i); }
        if(CreateExpeditionInstance($E[0], $E[1], $E[2], $E[3], $E[4], $E[5], $E[6], $E[7], $client->GetCleanName(), $client->CharacterID(), $E[8], $E[9], $E[10], $E[11], $E[12], $E[13], $E[14], $E[15], $E[16], $E[17], $E[18], $E[19])){ quest::assigntask($E[3]); }
    }
    if($popupid == 601){ #::: Send to Instance, usually when an instance is already created
        $connect = plugin::LoadMysql();
        my $InstID = $client->GetEntityVariable("InstID");
        $query = "SELECT
            instance_list.id,
            instance_list.zone,
            cust_ext_instances.x,
            cust_ext_instances.y,
            cust_ext_instances.z,
            cust_ext_instances.heading
            FROM
            instance_list
            INNER JOIN cust_ext_instances ON instance_list.id = cust_ext_instances.inst_id
            WHERE instance_list.id = '". $InstID . "'";
        if($Debug) { $What = "#::: CheckInstance #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
        $query_handle = $connect->prepare($query); $query_handle->execute();
        while (@row = $query_handle->fetchrow_array()){ ($zone, $X, $Y, $Z, $H) = ($row[1], $row[2], $row[3], $row[4], $row[5]); }
        quest::write("debug/instquery.txt", "#::: POPUPRESPONSE 601 #::: \n" . $query);
        #for($i=0;$i<=11;$i++){ $E[$i] = $client->GetEntityVariable("InstRequest" . $i); }
        #quest::say("SENDING TO INSTANCE $zone, $InstID, $X, $Y, $Z, $H");
        quest::MovePCInstance($zone, $InstID, $X, $Y, $Z, $H);
    }
    if($popupid == 602){ #::: Finalize Removing Self from Expedition
        $connect2 = plugin::LoadMysql();
        quest::crosszonesignalclientbyname($p2r, 604);
        my $p2r = $client->GetEntityVariable("expd_queue_remove_player");
        my $query = "DELETE FROM `cust_inst_players` WHERE `player_name` = '" . $p2r . "'";
        my $query_handle = $connect2->prepare($query); $query_handle->execute();
        my $taskid = $client->GetEntityVariable("expd_taskid_rem");
        my $expd_id = $client->GetEntityVariable("expd_id");
        NotifyExpeditionMembers($expd_id, $p2r . " has been removed from the expedition");
        if($taskid){ quest::crosszonesignalclientbyname($p2r, $taskid); }
    }
    if($popupid == 603){  #::: #expedition leave - finalize
        $connect2 = plugin::LoadMysql();
        $connect = plugin::LoadMysql();
        my @AdvInfo = LoadExpeditionInfo();
        my $query = "DELETE FROM `cust_inst_players` WHERE `player_name` = '" . $client->GetEntityVariable("expd_queue_leave_player") . "'";
        my $query_handle = $connect2->prepare($query); $query_handle->execute();
        if($Debug) { $What = "#::: Delete player #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
        if($client->GetEntityVariable("expd_queue_lead_change") > 0){ #::: Leader is leaving instance, re-elect another one
            my $query = "SELECT `player_name` FROM `cust_inst_players` WHERE `inst_id` = '" . $client->GetEntityVariable("expd_queue_lead_change") . "' ORDER BY `time_invited` LIMIT 1";
            my $query_handle = $connect2->prepare($query); $query_handle->execute();
            if($Debug) { $What = "#::: Find player #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
            while (@row = $query_handle->fetchrow_array()){
                my $query = "UPDATE `cust_inst_players` SET `is_leader` = '1' WHERE `player_name` = '" . $row[0] . "'";
                my $query_handle = $connect->prepare($query); $query_handle->execute();
                if($Debug) { $What = "#::: Elect new leader #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
                quest::crosszonesignalclientbyname($row[0], 606);
            }
        }
        $client->Message(15, "You have left your expedition");
        $client->FailTask($AdvInfo[3]);
        NotifyExpeditionMembers($AdvInfo[0], $client->GetCleanName() . " has left the expedition");
        if($AdvInfo[18] eq $zonesn && $instanceid > 0){ #::: He's most likely in the instance so lets kick them out
            quest::MovePCInstance($AdvInfo[12], $AdvInfo[14], $AdvInfo[15], $AdvInfo[16], $AdvInfo[17], 0);
        }
        $client->DelGlobal("ExpdInfo_" . $name); #::: Purge Expedition Cached info...
    }
    if($popupid == 604){ #::: Asking Leader if they really want to invite player (Of course)
        my $pname = $client->GetEntityVariable("expd_queue_invite_player");
        my $expdid = $client->GetEntityVariable("expd_queue_invite_expdid");
        $client->Message(15, "Invitation has been sent");
        quest::crosszonesignalclientbyname($pname, 602);
        quest::crosszonesignalclientbyname($pname, $expdid);
    }
    if($popupid == 605){ #::: Accept Instance Invitation
        $client->DelGlobal("ExpdInfo_" . $name); #::: Purge Expedition Cached info...
        my $expid = $client->GetEntityVariable("ExpdIDInvite");
        my $G2G = CheckForExpeditionRequirements($expid);
        if($G2G || $status > 200){
            FinalizeInstanceInvite($client->GetCleanName(), $expid, $client->CharacterID());
            @AdvInfo = LoadExpeditionInfo(); SynchronizeSharedTasks();
            if($AdvInfo[3]){ quest::assigntask($AdvInfo[3]); }
            $client->Message(15, "You have been assigned to expedition '". $AdvInfo[4] . "'");
            NotifyExpeditionMembers($expid, $client->GetCleanName() . " has been added to the expedition");
        }
    }
    if($popupid == 606){ #::: Elect new leader
        @AdvInfo = LoadExpeditionInfo();
        my $NewLeader = $client->GetEntityVariable("expd_queue_elect_leader");
        NotifyExpeditionMembers($AdvInfo[0], $NewLeader . " has been made the new expedition leader");
        my $query = "UPDATE `cust_inst_players` SET `is_leader` = '1' WHERE `player_name` = '" . $NewLeader . "'"; my $query_handle = $connect->prepare($query); $query_handle->execute();
        my $query = "UPDATE `cust_inst_players` SET `is_leader` = '0' WHERE `player_name` = '" . $client->GetCleanName() . "'"; my $query_handle = $connect->prepare($query); $query_handle->execute();
        @AdvInfo = LoadExpeditionInfo(1);
        quest::crosszonesignalclientbyname($NewLeader, 607);
    }
    #::: END: Instance/expedition plugin code section #:::
}
 
#::: Routine to check if client meets expedition requirements
sub CheckForExpeditionRequirements{
    $connect = plugin::LoadMysql();
    $query = "SELECT
        CEILING(AVG(`cust_expd_player_cache`.level)) AS `AVG`,
        Count(*) AS `COUNT`,
        cust_ext_instances.`limit`,
        cust_ext_instances.avglevelreq,
        cust_expd_player_cache.id,
        cust_expd_player_cache.name,
        cust_expd_player_cache.level,
        cust_expd_player_cache.timelaston,
        cust_ext_instances.req_players,
        cust_ext_instances.inst_id
        FROM
        cust_expd_player_cache
        Inner Join cust_inst_players ON cust_expd_player_cache.id = cust_inst_players.char_id
        Inner Join cust_ext_instances ON cust_inst_players.inst_id = cust_ext_instances.inst_id
        WHERE cust_ext_instances.inst_id = ?";
    $query_handle = $connect->prepare($query); $query_handle->execute($_[0]);
    $client->Message(15, "Expedition ID: " . $_[0]);
    while (@row = $query_handle->fetchrow_array()){
        if($row[3] > 0){ #::: There is a level requirement, do math
            if((($row[0] + $ulevel) / 2) > $row[3]){ } else{ $client->Message(15, "You do not meet the level requirements for this - Average Level Requirement: " . $row[3]); return 0; }
        }
        if(($row[1] + 1) > $row[2]){ $client->Message(15, "There are too many players in this expedition already, the max is " . $row[2] . " players"); return 0; }
    }
    return 1;
}
 
#::: Remove player from expedition routine
sub ExpeditionProcessRemove{
    $p2r = $_[0];
    @AdvInfo = LoadExpeditionInfo();
    if($AdvInfo[2] == 1){ #::: Checks for leadership
        if($p2r eq $name){ $client->Message(15, "You can't remove yourself as leader, if you wish to leave use #expedition leave"); return; }
        $client->Message(15, "Searching for player '" . $p2r . "'");
        $connect2 = plugin::LoadMysql();
        my $query = "SELECT
            cust_inst_players.inst_id,
            cust_inst_players.player_name
            FROM
            cust_inst_players
            Inner Join cust_ext_instances ON cust_inst_players.inst_id = cust_ext_instances.inst_id
            WHERE cust_inst_players.player_name LIKE '%". $p2r . "%' AND cust_inst_players.inst_id = '" . $AdvInfo[0] . "'";
        if($Debug) { $What = "#::: ExpeditionProcessRemove #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
        $Found = 0;
        my $query_handle = $connect2->prepare($query); $query_handle->execute();
        while (@row = $query_handle->fetchrow_array()){ $Found = 1; $pname = $row[1]; }
        if($Found == 1){ $client->SetEntityVariable("expd_id", $AdvInfo[0]); $client->SetEntityVariable("expd_taskid_rem", $AdvInfo[3]); $client->SetEntityVariable("expd_queue_remove_player", $pname); quest::popup("Expedition: Remove Player '" . $pname . "'", "Are you sure you want to remove player '" . $pname . "'?", 602, 1); }else { $client->Message(15, "Player '" . $p2r ."' not found"); }
    }
    else{ $client->Message(15, "You are not the leader of any expedition currently..."); }
    $pname = undef;
}
 
#::: Count current expedition player amount
sub CountExpeditionPlayers{
    $connect = plugin::LoadMysql();
    my $query = "SELECT COUNT(`char_id`) FROM `cust_inst_players` WHERE `inst_id` = '" . $_[0] . "';";
    $query_handle = $connect->prepare($query); $query_handle->execute(); my @Members;
    while (@row = $query_handle->fetchrow_array()){ return $row[0] }
}
 
#::: Process group invite for selected player, invite them and their group
sub ExpeditionProcessGroupInvite {
    $p2r = $_[0];
    @AdvInfo = LoadExpeditionInfo();
    my $AvgLevel = 0; $Found = 0;
    if($AdvInfo[2] == 1){ #::: Checks for leadership
        $client->Message(15, "Inviting player's group '" . $p2r . "'");
        $connect2 = plugin::LoadMysql();
        my $query = "SELECT `name`, `level` FROM `cust_expd_player_cache` WHERE `name` LIKE ? LIMIT 1;";
        my $query_handle = $connect2->prepare($query); $query_handle->execute($p2r);
        while (@row = $query_handle->fetchrow_array()){ $Found = 1; $pname = $row[0]; $newplevel = $row[1]; }
        if($Found == 1){
            $I_GID = 0;
            my $query = "SELECT
                group_id.groupid
                FROM
                cust_expd_player_cache
                Inner Join group_id ON cust_expd_player_cache.id = group_id.charid
                WHERE cust_expd_player_cache.name LIKE '%" . $pname . "%'
                ";
            my $query_handle = $connect2->prepare($query); $query_handle->execute();
            while (@row = $query_handle->fetchrow_array()){ $I_GID = $row[0]; }
            $pnames = "";
            my $query = "SELECT
                group_id.groupid,
                group_id.charid,
                group_id.name
                FROM
                group_id WHERE groupid = ?";
            my $query_handle = $connect2->prepare($query); $query_handle->execute($I_GID);
            while (@row = $query_handle->fetchrow_array()){
                if(!$qglobals{"ExpdInfo_" . $row[2]}){
                    $pnames .= $row[2] . ", ";
                    quest::crosszonesignalclientbyname($row[2], 602);
                    quest::crosszonesignalclientbyname($row[2], $AdvInfo[0]);
                }else{ $client->Message(15, $row[2] . " is currently in an expedition...");}
            }
            $client->Message(15, "Invitations have been sent to " . substr($pnames, 0, -2));
        }else { $client->Message(15, "Player '" . $p2r ."' not found"); }
    }
    else{ $client->Message(15, "You are not the leader of any expedition currently..."); }
    $pname = undef;
}
 
#::: Process singular invite for a single player
sub ExpeditionProcessInvite {
    $p2r = $_[0];
    @AdvInfo = LoadExpeditionInfo();
    my $AvgLevel = 0;
    if($AdvInfo[2] == 1){ #::: Checks for leadership
        $client->Message(15, "Searching for player '" . $p2r . "'");
        $connect2 = plugin::LoadMysql();
        my $query = "SELECT `name`, `level` FROM `cust_expd_player_cache` WHERE `name` LIKE '%". $p2r . "%' LIMIT 1;";
        if($Debug) { $What = "#::: ExpeditionProcessInvite #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
        #$Found = 1;
        #quest::say($query);
        my $query_handle = $connect2->prepare($query); $query_handle->execute();
        while (@row = $query_handle->fetchrow_array()){ $Found = 1; $pname = $row[0]; $newplevel = $row[1]; }
        if($Found == 1){
            if(!$qglobals{"ExpdInfo_" . $pname}){
                if($AdvInfo[5]){ #::: We have a level requirement, check for it
                    if($Debug){ $client->Message(15, "DEBUG: New player Level is : ". $newplevel); }
                    if($Debug){ $client->Message(15, "DEBUG: Player Lvl Req is: ". $AdvInfo[5]); }
                    $AvgLevel = LoadExpeditionAverageLevel($AdvInfo[0]); #::: Get current average level of players
                    if($Debug){ $client->Message(15, "DEBUG: Current exp avg lvl : ". ($AvgLevel + $newplevel / 2)); }
                    if($Debug){ $client->Message(15, "DEBUG: Current exp avg after new player: ". $AvgLevel); }
                }
                if($AdvInfo[10]){ #::: We have a player cap, check for it
                    $ExpdPlayers = CountExpeditionPlayers($AdvInfo[0]); #::: Get amount of expedition players
                }
                my $NewALVL = (($AvgLevel + $newplevel) / 2);
                if($NewALVL > $AdvInfo[5] || $AvgLevel == 0){
                    if($ExpdPlayers + 1 > $AdvInfo[10]){
                        $client->Message(15, "Inviting this player would exceed your expedition limit of " . $AdvInfo[10] . " players");
                    }else{
                        quest::popup("Expedition: Invite Player '" . $pname . "'", "Are you sure you want to invite player '" . $pname . "'?", 604, 1);
                        $client->SetEntityVariable("expd_queue_invite_player", $pname);
                        $client->SetEntityVariable("expd_queue_invite_expdid", $AdvInfo[0]);
                    }
                }else{
                    $client->Message(15, "Inviting this player would not meet the average level requirements needed for this expedition: " . $AdvInfo[5] . " current average level is ". $AvgLevel . " with new player it would be " . int($NewALVL));
                }
            }else{ $client->Message(15, $pname . " is already in an expedition, you cannot invite them!"); }
        }else { $client->Message(15, "Player '" . $p2r ."' not found"); }
    }
    else{ $client->Message(15, "You are not the leader of any expedition currently..."); }
    $pname = undef;
}
 
#::: Routine to make targeted player as leader of expedition
sub ExpeditionMakeLeader{
    $p2r = $_[0];
    @AdvInfo = LoadExpeditionInfo(1);
    my $AvgLevel = 0;
    if($AdvInfo[2] == 1){ #::: Checks for leadership
        my $query = "SELECT
            cust_inst_players.inst_id,
            cust_inst_players.player_name
            FROM
            cust_inst_players
            Inner Join cust_ext_instances ON cust_inst_players.inst_id = cust_ext_instances.inst_id
            WHERE cust_inst_players.player_name LIKE '%". $p2r . "%' AND cust_inst_players.inst_id = '" . $AdvInfo[0] . "'";
        if($Debug) { $What = "#::: ExpeditionProcessRemove #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
        $Found = 0;
        my $query_handle = $connect2->prepare($query); $query_handle->execute();
        while (@row = $query_handle->fetchrow_array()){ $Found = 1; $pname = $row[1]; }
        if($pname eq $client->GetCleanName()){ $client->Message(15, "You are already the leader!"); }
        elsif($Found == 1){ $client->SetEntityVariable("expd_id", $AdvInfo[0]);  $client->SetEntityVariable("expd_queue_elect_leader", $pname); quest::popup("Expedition: New Leader '" . $pname . "'", "Are you sure you want to make player '" . $pname . "' the new expedition leader?", 606, 1); }else { $client->Message(15, "Player '" . $p2r ."' not found"); }
    }
    else{ $client->Message(15, "You are not the leader of any expedition currently..."); }
    $pname = undef;
}
 
#::: Routing to process Expedition leave
sub ExpeditionLeave{
    $p2r = $_[0];
    @AdvInfo = LoadExpeditionInfo(1);
    if($AdvInfo[0]){ #::: Checks for membership
        $client->SetEntityVariable("expd_queue_leave_player", $AdvInfo[1]); quest::popup("Expedition: Leave", "Are you sure you want to leave your current expedition?", 603, 1); if($AdvInfo[2] == 1){ $client->SetEntityVariable("expd_queue_lead_change", $AdvInfo[0]); }
    }
    else{ $client->Message(15, "You are not the member of an expedition currently..."); }
    $pname = undef;
}
 
#::: Process current Expedition level, expedition ID is passed
sub LoadExpeditionAverageLevel{
    $ExpdID = $_[0];
    $connect2 = plugin::LoadMysql();
    my $query = "SELECT AVG(`cust_expd_player_cache`.level) FROM `cust_expd_player_cache` Inner Join cust_inst_players ON cust_inst_players.char_id = `cust_expd_player_cache`.id WHERE cust_inst_players.inst_id LIKE '%". $ExpdID . "%'";
    if($Debug) { $What = "#::: LoadExpeditionAverageLevel #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
    my $query_handle = $connect2->prepare($query); $query_handle->execute();
    while (@row = $query_handle->fetchrow_array()){ return int($row[0]); }
}
 
### Load Expedition into QGlobal
sub LoadExpeditionInfo{
    $connect2 = plugin::LoadMysql();
    if(!$_[0] == 1){ #::: If set to 1, we want to re-read from the database and cache again
        if($qglobals{"ExpdInfo_" . $name}){ @ExpdInfo = split(',', $qglobals{"ExpdInfo_" . $name}); return @ExpdInfo; } #::: Caching Expedition Info for very fast responses
    }
    my $query = "SELECT
        cust_inst_players.inst_id,
        cust_inst_players.player_name,
        cust_inst_players.is_leader,
        cust_ext_instances.task_assoc,
        cust_ext_instances.inst_name,
        cust_ext_instances.avglevelreq,
        cust_ext_instances.ID,
        cust_ext_instances.shared_task,
        cust_ext_instances.duration,
        cust_ext_instances.expdate,
        cust_ext_instances.limit,
        cust_ext_instances.lockout,
        cust_ext_instances.return_zone,
        cust_ext_instances.return_version,
        cust_ext_instances.return_instanceid,
        cust_ext_instances.return_x,
        cust_ext_instances.return_y,
        cust_ext_instances.return_z,
        cust_ext_instances.zonesn,
        cust_ext_instances.boot_on_completion
        FROM
        cust_inst_players
        Inner Join cust_ext_instances ON cust_inst_players.inst_id = cust_ext_instances.inst_id
        WHERE cust_inst_players.player_name LIKE '%". $name . "%' LIMIT 1";
    if($Debug) { $What = "#::: LoadExpeditionInfo #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
    my $query_handle = $connect2->prepare($query); $query_handle->execute(); my $NV = "";
    while (@row = $query_handle->fetchrow_array()){  foreach my $val (@row) { $NV .= "$val,"; } quest::setglobal("ExpdInfo_" . $name, substr ($NV, 0, -1), 7, "S" . ($row[9] - time)); return @row;  }
}
 
sub ExpeditionMemberList{
    $connect = plugin::LoadMysql();
    if(!$_[1]){
        @AdvInfo = LoadExpeditionInfo();
        $ExpdID = $AdvInfo[0];
    }else{ $ExpdID = $_[1]; }
    $query = "SELECT
        instance_list.zone,
        instance_list.version,
        instance_list.start_time,
        instance_list.duration,
        cust_ext_instances.identifier,
        cust_ext_instances.type,
        cust_ext_instances.`limit`,
        cust_ext_instances.task_assoc,
        cust_ext_instances.inst_name,
        cust_inst_players.player_name,
        cust_inst_players.pending_invite,
        cust_inst_players.is_leader,
        cust_ext_instances.inst_id
        FROM
        instance_list
        INNER JOIN cust_ext_instances ON instance_list.id = cust_ext_instances.inst_id
        INNER JOIN cust_inst_players ON cust_ext_instances.inst_id = cust_inst_players.inst_id
        WHERE cust_ext_instances.inst_id = '". $ExpdID . "'
        ORDER BY cust_inst_players.is_leader DESC, cust_inst_players.pending_invite;";
        if($Debug) { $What = "#::: DisplayInstanceQueue #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);}
        $query_handle = $connect->prepare($query); $query_handle->execute();
        $n = 0; $Players = "";
    while (@row = $query_handle->fetchrow_array()){
        ($Zone, $Version, $Start_Time, $Duration, $Ident, $Type, $Limit, $Task_Assoc, $inst_name, $player_name, $pending_invite, $is_leader) = ($row[0], $row[1], $row[2], $row[3], $row[4], $row[5], $row[6], $row[7], $row[8], $row[9], $row[10], $row[11]); $n++;
        if($is_leader == 1){ $L = " - <c \"#80FF00\">Leader</c>"; } else{ $L = "" };
        if($pending_invite == 1){ $L = " - Pending"; } else{ $P = "" };
        $Players .= "" . $n . ") " . $player_name . $L . $P . "<br>";
    }
    if($Zone ne ""){
        if($Task_Assoc > 0){
            $query_handle = $connect->prepare("SELECT title, description, reward, startzone, minlevel, maxlevel, `repeatable` FROM `tasks` WHERE `id` = '" . $Task_Assoc . "' LIMIT 1;"); $query_handle->execute();
            while (@row = $query_handle->fetchrow_array()){ ($TTitle, $TDesc) = ($row[0], $row[1]); }
        }
        if($TDesc=~/\[1/i){ #::: There are multiple steps in the description
            $TDesc =~ s/\]//g; $TDesc =~ s/\[//g;
            @TDesc2 = split(',', $TDesc);
            foreach my $val (@TDesc2) {
                if($val=~ /^[+-]?\d+$/){}
                else{ $TDesc = substr($val, 0, -1);  last;}
            }
        }
        $TBody = "<c \"#FFFC17\">". $inst_name . "</c><br> <table><tr><td>
            <tr><td><c \"#00FF00\">Time Left</c></td><td>". plugin::GetTimeLeftAdv($Start_Time + $Duration) . "</td></tr>
            <tr><td><c \"#00FF00\">Members</c></td><td>". $n . "/". $Limit . " (". $Type . ")</td></tr>
            </td></tr></table>-------------------------------------<br>
            " . $Players . "<br>
            -------------------------------------<br>
            <c \"#FFFC17\">" . $TTitle . "</c><br>
            &nbsp;&nbsp;&nbsp;&nbsp; - " . $TDesc . "<br><br>";
        if(!$_[1]){ $TBody .= "<c \"#F07F00\">Click 'Ok' to Close this Window.</c>"; $Buttons = 0; $PID = 0; }
        if($_[1]){ $TBody .= "<c \"#F07F00\">Click 'Yes' to Accept this Invitation.</c>"; $Buttons = 1; $PID = 605; }
        quest::popup($inst_name, $TBody, $PID, $Buttons);
    } else{ $client->Message(15, "It doesn't appear that you have an active expedition!"); }
}
 
sub FinalizeInstanceInvite{
    $connect = plugin::LoadMysql();
    $CharName = $_[0]; $InstID = $_[1]; $CharID = $_[2];
    $query = "REPLACE INTO `cust_inst_players` (`inst_id`, `char_id`, `player_name`, `pending_invite`, `is_leader`, time_invited) VALUES (?, ?, ?, ?, ?, NOW());";
    $query_handle = $connect->prepare($query); $query_handle->execute($InstID, $CharID, $CharName, 0, 0);
    $query = "REPLACE INTO `instance_list_player` (`id`, `charid`) VALUES (?, ?);";
    $query_handle = $connect->prepare($query); $query_handle->execute($InstID, $CharID);
}
 
sub CheckForSharedTaskUpdates{
    @TaskProg = GetTaskProgress($_[0]);
    @AdvInfo = LoadExpeditionInfo();
    my $n = 0;
    foreach my $val (@TaskProg){
        my $RecUpd = $TaskProg[$n]; my $Prog = quest::gettaskactivitydonecount($AdvInfo[3], $n);
        if($RecUpd > $Prog){
            if($Debug) { $client->Message(15, "Debug Stored progress is greater than mine, lets catch up"); }
            quest::updatetaskactivity($AdvInfo[3], $n, ($RecUpd - $Prog));
        }
        $n++;
    }
}
 
#::: Snychronize Task Progress with other players
sub SynchronizeSharedTasks{
    if(!@AdvInfo){ @AdvInfo = LoadExpeditionInfo(); }
    my @TaskInf = GetTaskInfo($AdvInfo[6]);
    if($AdvInfo[3] != 0 && $TaskInf[1] != 1){
        if(!quest::istaskactive($AdvInfo[3])){
            quest::assigntask($AdvInfo[3]);
        }
    }
    if($AdvInfo[3] != 0 && $TaskInf[1] != 1){
        @TaskProg = GetTaskProgress($AdvInfo[6]);
        $n = 0;
        foreach $val (@TaskProg){
            my $RecUpd = $TaskProg[$n];
            my $Prog = quest::gettaskactivitydonecount($AdvInfo[3], $n);
            if($RecUpd > $Prog){
                if($Debug) { $client->Message(15, "Debug Stored progress is greater than mine, lets catch up"); }
                quest::updatetaskactivity($AdvInfo[3], $n, ($RecUpd - $Prog));
            }
            $n++;
        }
    }
}
 
#::: This is a routine that is executed when an expedition has been accepted
#::: It will insert a record into `cust_inst_players` with the player name, usually this is executed by the creator
sub CreateExpeditionInstance{
    $connect = plugin::LoadMysql();
    $connect2 = plugin::LoadMysql();
    #::: InitInstance Variables are recalled here - 3rd passing
    my ($Ident, $Type, $Limit, $Task_Assoc, $Title, $Duration, $Version, $ZoneSN, $CName, $CID, $X, $Y, $Z, $H, $AvgLevel, $ReqPlayers, $IsSharedTask, $Lockout, $Bootoncomp, $CompX, $CompY, $CompZ) = ($_[0], $_[1], $_[2], $_[3], $_[4], $_[5], $_[6], $_[7], $_[8], $_[9], $_[10], $_[11], $_[12], $_[13], $_[14], $_[15], $_[16], $_[17], $_[18], $_[19], $_[20], $_[21]);
    my $InstID = quest::CreateInstance($ZoneSN, $Version, $Duration);
    if($InstID > 0){
        #::: Hack attempt #:::
        @Invitees = GetExpeditionInvitees($client->GetCleanName());
        $n = 0;
        while($Invitees[$n][0]){ $n++; }
        if($n > $Limit){ $client->Message(15, "Expedition creation failure: You have " . $n . " members in your party, limit is " . $Limit); return; }
         
        #::: Insert Leader into Expedition and create the Expedition #:::
        $query_handle = $connect->prepare("INSERT INTO `cust_inst_players` (inst_id, char_id, player_name, pending_invite, is_leader, time_invited) VALUES ('" . $InstID . "', '" . $CID . "', '" . $CName . "', '0', '1', NOW());"); $query_handle->execute();
        $query_handle = $connect->prepare("INSERT INTO `cust_ext_instances` (`inst_id`, `identifier`, `type`, `limit`, `task_assoc`, `inst_name`, `zonesn`, `x`, `y`, `z`, `heading`, `avglevelreq`, `req_players`, `shared_task`, `duration`, `expdate`, `lockout`, `return_zone`, `return_version`, `return_instanceid`, `return_x`, `return_y`, `return_z`, `boot_on_completion`) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, UNIX_TIMESTAMP() + $Duration, ?, ?, ?, ?, ?, ?, ?, ?);"); $query_handle->execute($InstID, $Ident, $Type, $Limit, $Task_Assoc, $Title, $ZoneSN, $X, $Y, $Z, $H, $AvgLevel, $ReqPlayers, $IsSharedTask, $Duration, $Lockout, $zoneid, $instanceversion, $instanceid, int($client->GetX()), int($client->GetY()), int($client->GetZ()), $Bootoncomp);
        $query_handle = $connect->prepare("INSERT INTO `instance_list_player` (`id`, `charid`) VALUES (?, ?);"); $query_handle->execute($InstID, $CID);
         
        #::: Invite Expedition Members #:::
        $n = 0;
        while($Invitees[$n][0]){
            #quest::say($Invitees[$n][0] . " " . $Invitees[$n][1]);
            $CID = $Invitees[$n][0]; $CName = $Invitees[$n][1];
            if($CName ne $name){
                $query_handle = $connect->prepare("INSERT INTO `cust_inst_players` (inst_id, char_id, player_name, pending_invite, is_leader, time_invited) VALUES ('" . $InstID . "', '" . $CID . "', '" . $CName . "', '0', '0', NOW());"); $query_handle->execute();
                $query_handle = $connect->prepare("INSERT INTO `instance_list_player` (`id`, `charid`) VALUES (?, ?);"); $query_handle->execute($InstID, $CID);
            }
            quest::crosszonesignalclientbycharid($CID, 600);
            $CompC = $entity_list->GetClientByCharID($CID);
            if($CompC){ $CompC->MarkCompassLoc($CompX, $CompY, $CompZ); }
            $n++;
        }
        if($n == 0){
            quest::crosszonesignalclientbycharid($client->CharacterID(), 600);
            $client->MarkCompassLoc($CompX, $CompY, $CompZ);
        }
        if($IsSharedTask == 1){ #::: This is a shared task so we need to centralize the progress to a table
            if($Debug){ $client->Message(15, "DEBUG: This is a shared task"); }
            my @AdvInfo = LoadExpeditionInfo();
            my $query = "SELECT `activityid` FROM `activities` WHERE `taskid` = '". $Task_Assoc . "'";
            $query_handle = $connect->prepare($query); $query_handle->execute();
            if($Debug) { $What = "#::: Load Task Data #::: "; $client->Message(8, $What . " " . $query); quest::write("debug/instquery.txt", $What . "\n" . $query);} my $NV = "";
            while (@row = $query_handle->fetchrow_array()){  $NV .= "0,"; }
            quest::setglobal("ExpdSharedTask_" . $AdvInfo[6], $AdvInfo[3] . ",0", 7, "S" . $Duration); #::: StoreTaskID and completion bit
            quest::setglobal("ExpdSharedTaskProg_" . $AdvInfo[6], substr ($NV, 0, -1), 7, "S" . $Duration); #::: Store Task Progress
        }
        $client->Message(15, "Expedition has been created successfully");
        return 1;
    }else{ $client->Message(13, "Expedition has failed to create, please contact your server operator");  return; }
}
 
#::: This subroutine will get the members in groups/raids
sub GetExpeditionInvitees {
    $connect = plugin::LoadMysql();
    my @ToInvite;
    if($client->GetRaid()){
        $query = "SELECT `raidid` FROM `raid_members` WHERE `name` = '". $_[0] . "';";
        $query_handle = $connect->prepare($query); $query_handle->execute(); while (@row = $query_handle->fetchrow_array()){ $GPID = $row[0]; }
        $query = "SELECT `charid`, `name` FROM `raid_members` WHERE `groupid` = '". $GPID . "';";
        $query_handle = $connect->prepare($query); $query_handle->execute(); while (@row = $query_handle->fetchrow_array()){  push(@ToInvite, [$row[0], $row[1]]); }
    }
    elsif($client->GetGroup()){
        $query = "SELECT groupid FROM group_id WHERE `name` = '". $_[0] . "';";
        $query_handle = $connect->prepare($query); $query_handle->execute(); while (@row = $query_handle->fetchrow_array()){ $GPID = $row[0]; }
        $query = "SELECT charid, name FROM group_id WHERE `groupid` = '". $GPID . "';";
        $query_handle = $connect->prepare($query); $query_handle->execute(); while (@row = $query_handle->fetchrow_array()){ push(@ToInvite, [$row[0], $row[1]]);  }
        return @ToInvite;
    }
}
 
sub NotifyExpeditionMembers{
    $connect = plugin::LoadMysql();
    my $query = "SELECT `char_id`, `player_name` FROM `cust_inst_players` WHERE `inst_id` = '". $_[0] . "';";
    $query_handle = $connect->prepare($query); $query_handle->execute();
    while (@row = $query_handle->fetchrow_array()){  quest::crosszonemessageplayerbyname(15, $row[1], $_[1]); }
}
 
sub GetTaskInfo{ if($qglobals{"ExpdSharedTask_" . $_[0]}){ my @ExpdInfo = split(',', $qglobals{"ExpdSharedTask_" . $_[0]}); return @ExpdInfo; } }
sub GetTaskProgress{ if($qglobals{"ExpdSharedTaskProg_" . $_[0]}){ @ExpdInfo = split(',', $qglobals{"ExpdSharedTaskProg_" . $_[0]}); return @ExpdInfo; } }
 
#::: Function to store activity definitions for task, so that they can by force synced on task stage completion
sub GetTaskActivityDefs{
    my $NV = "";
    if($qglobals{"ExpdSharedTaskActSync_" . $_[0]}){
        @ExpdInfo = split(',', $qglobals{"ExpdSharedTaskActSync_" . $_[0]});
        foreach $val (@ExpdInfo){ $NV .= "$val,"; }
        #$client->Message(15, "Cached " . substr ($NV, 0, -1));
        return @ExpdInfo;
    }else{
        $connect = plugin::LoadMysql();
        my $query = "SELECT `activityid`, `goalcount` FROM `activities` WHERE `taskid` = '". $_[0] . "' ORDER BY `activityid`;";
        $query_handle = $connect->prepare($query); $query_handle->execute();
        while (@row = $query_handle->fetchrow_array()){ $NV .= "$row[1],";  }
        #$client->Message(15, substr ($NV, 0, -1));
        quest::setglobal("ExpdSharedTaskActSync_" . $_[0], substr ($NV, 0, -1), 7, "S" . ($_[1] - time));
    }
}
sub GetExpdMembers{
    $connect = plugin::LoadMysql();
    my $query = "SELECT `char_id` FROM `cust_inst_players` WHERE `inst_id` = '" . $_[0] . "';";
    $query_handle = $connect->prepare($query); $query_handle->execute(); my @Members;
    while (@row = $query_handle->fetchrow_array()){ push(@Members, $row[0]); }
    return @Members;
}
 
#########################################
#::: END Expedition System - Include :::#
#########################################
```
{% endtab %}
{% endtabs %}

* When you have that in place, you will need all of the handlers hooked into your global\_player.pl, it does not matter where you place any of them but you will need Expdhandler\_TASK\_STAGE\_COMPLETE at the bottom of 'TASK\_STAGE\_COMPLETE'

{% tabs %}
{% tab title="Perl" %}
```perl
sub EVENT_ENTERZONE {
    ExpdHandler_EVENT_ENTERZONE(); #::: Expedition Enter Zone Handler
}
 
sub EVENT_POPUPRESPONSE{
    ExpdHandler_EVENT_POPUPRESPONSE(); #::: Expedition system - EVENT_POPUPRESPONSE
}
 
sub EVENT_SAY{
    ExpdHandler_EVENT_SAY(); #::: Expedition Parser - EVENT_SAY
}
 
sub EVENT_SIGNAL{
    ExpdHandler_EVENT_SIGNAL();  #::: Expedition system
}
 
sub EVENT_TASK_COMPLETE{
    ExpdHandler_EVENT_TASK_COMPLETE(); #::: Has to be last in EVENT_TASK_COMPLETE
}
sub EVENT_TASK_UPDATE{
    ExpdHandler_EVENT_TASK_UPDATE(); #::: EVENT_TASK_UPDATE Expedition processing
}
 
sub EVENT_DISCONNECT{
    ExpdHandler_EVENT_DISCONNECT();
    plugin::DumpPlayerCache(0); #::: Dump Player Info into Cache
}
 
sub EVENT_CONNECT{
    plugin::DumpPlayerCache(1); #::: Dump Player Info into Cache
}
```
{% endtab %}
{% endtabs %}

## **The Database Tables**

* You will need the following custom tables in order for this to work:
  * **cust\_inst\_players** - Contains the players and what instances they belong to \(Expeditions\)
  * **cust\_ext\_instances** - Contains general instance info \(Expeditions\)
  * **cust\_expd\_player\_cache** - Contains quick table lookup information so the character\_ table is not queried. Contains Level, Character Name as well as online/offline status
  * **cust\_expd\_completion\_records** - Only if you use the completion function in plugins will this table come into any sort of reference
  * **cust\_ext\_hist\_lockouts** - Contains player lockouts for an expedition \(History reference only\)
  * **cust\_ext\_lockouts** - Contains enforced player lockouts, meaning a player cannot actually get another expedition of a similar 'Namespace' until that expedition has expired
* Shared tasks info is done completely through multiple complex qglobals. This makes the system very fast since all common data is referenced in quest globals \(Memory\)

{% tabs %}
{% tab title="Query" %}
```sql
SET FOREIGN_KEY_CHECKS=0;
 
-- ----------------------------
-- Table structure for cust_expd_completion_records
-- ----------------------------
DROP TABLE IF EXISTS `cust_expd_completion_records`;
CREATE TABLE `cust_expd_completion_records` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(50) DEFAULT NULL,
  `expedition` varchar(80) DEFAULT NULL,
  `completed_secs` int(11) DEFAULT NULL,
  `completed_mins` int(11) DEFAULT NULL,
  `completion_time` timestamp NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1686 DEFAULT CHARSET=utf8;
 
-- ----------------------------
-- Table structure for cust_expd_player_cache
-- ----------------------------
DROP TABLE IF EXISTS `cust_expd_player_cache`;
CREATE TABLE `cust_expd_player_cache` (
  `id` int(11) DEFAULT NULL,
  `name` varchar(75) NOT NULL DEFAULT '',
  `level` int(11) DEFAULT NULL,
  `timelaston` int(11) unsigned DEFAULT NULL,
  `online` int(11) DEFAULT NULL,
  PRIMARY KEY (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
 
-- ----------------------------
-- Table structure for cust_ext_hist_lockouts
-- ----------------------------
DROP TABLE IF EXISTS `cust_ext_hist_lockouts`;
CREATE TABLE `cust_ext_hist_lockouts` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `player` varchar(75) NOT NULL DEFAULT '',
  `lockout_name` varchar(75) NOT NULL DEFAULT '',
  `lockout_expire` int(11) DEFAULT '0',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2453 DEFAULT CHARSET=utf8;
 
-- ----------------------------
-- Table structure for cust_ext_instances
-- ----------------------------
DROP TABLE IF EXISTS `cust_ext_instances`;
CREATE TABLE `cust_ext_instances` (
  `ID` int(11) NOT NULL AUTO_INCREMENT,
  `inst_id` int(11) NOT NULL DEFAULT '0',
  `identifier` varchar(100) DEFAULT NULL,
  `type` varchar(25) DEFAULT NULL,
  `limit` int(11) DEFAULT '0',
  `task_assoc` int(11) DEFAULT '0',
  `inst_name` varchar(40) DEFAULT NULL,
  `zonesn` varchar(40) DEFAULT NULL,
  `x` float DEFAULT NULL,
  `y` float DEFAULT NULL,
  `z` float DEFAULT NULL,
  `return_zone` int(11) DEFAULT NULL,
  `return_version` int(11) DEFAULT NULL,
  `return_instanceid` int(11) DEFAULT NULL,
  `return_x` float DEFAULT NULL,
  `return_y` float DEFAULT NULL,
  `return_z` float DEFAULT NULL,
  `heading` float DEFAULT NULL,
  `avglevelreq` int(11) DEFAULT NULL,
  `req_players` int(11) DEFAULT '0',
  `shared_task` int(11) DEFAULT '0',
  `duration` int(11) DEFAULT '0',
  `expdate` int(11) DEFAULT '0',
  `lockout` int(11) DEFAULT '0',
  `boot_on_completion` int(11) DEFAULT '0',
  PRIMARY KEY (`ID`)
) ENGINE=InnoDB AUTO_INCREMENT=44 DEFAULT CHARSET=utf8;
 
-- ----------------------------
-- Table structure for cust_ext_lockouts
-- ----------------------------
DROP TABLE IF EXISTS `cust_ext_lockouts`;
CREATE TABLE `cust_ext_lockouts` (
  `player` varchar(75) NOT NULL DEFAULT '',
  `lockout_name` varchar(75) NOT NULL DEFAULT '',
  `lockout_expire` int(11) DEFAULT '0',
  PRIMARY KEY (`player`,`lockout_name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
 
-- ----------------------------
-- Table structure for cust_inst_players
-- ----------------------------
DROP TABLE IF EXISTS `cust_inst_players`;
CREATE TABLE `cust_inst_players` (
  `inst_id` int(11) NOT NULL DEFAULT '0',
  `char_id` int(11) DEFAULT NULL,
  `player_name` varchar(40) NOT NULL DEFAULT '',
  `pending_invite` int(1) DEFAULT '0',
  `is_leader` int(1) DEFAULT '0',
  `time_invited` timestamp NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`inst_id`,`player_name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
{% endtab %}
{% endtabs %}

## Using the System

* Once you have everything in place and installed, the engine is carried by a simple initialization quest
* Everything you need to create your instance and everything that it enforces happens on plugin::InitInstanceQueue

## **Examples**

{% tabs %}
{% tab title="Perl" %}
```perl
sub EVENT_SAY {
        if($text=~/hail/i) {
            plugin::DiaWind("{r}Bark! Bark! Grrr~. I remember a time when we envaded {y}Qeynos~ because a {r}crooked guard killed one of our kind~,
            it caused them to {r}declare war~ and they {lb}completely annihilated our entire clan~. It was not good... [I will investigate> +44+");
        } elsif($text=~/i will investigate/i) {
            if($status > 200) {
				$ReqPlayer = 1;
			} else {
				$ReqPlayer = 4;
			}
            @AdvInfo = plugin::LoadExpeditionInfo2();
			plugin::CheckForStaleInstances();
            if($AdvInfo[0] > 0) {
				plugin::DisplayInstanceQueue($AdvInfo[0]);
			} else {
                plugin::InitInstanceQueue(
					"Blackburrow Invasion", #Instance Identifier
                    "Group", #Description of Adventure (Ex: Group)
                    6, #Number of Players
                    168, #Task ID Association
                    "Blackburrow Invasion", #Description of Adventure
                    21600, #Duration Timer (Seconds)
                    1, #Version
                    "oldblackburrow", #ZoneSN
                    24, #Instance Destination X
                    -369, #Instance Destination Y
                    46, #Instance Destination Z
                    0, #Instance Destination H
                    190, #Required Average Level
                    $ReqPlayer, #Minimum # of Players
                    1, #Is Shared Task (0/1)
                    1800, #Lockout Duration
                    0, ### Boot on completion
                    721, # X Compass Loc
                    -746, # Y Compass Loc
                    206, # Z Compass Loc
                );
            }
        }
    }
}
```
{% endtab %}
{% endtabs %}

* You can initiate an expedition from any event, it could be on proximity walkup of an NPC, it could be clicking a door. As long as you have the same general format that I have listed above you will be solid
* The moment you hail or trigger **plugin::InitInstanceQueue**, you will get a popup window that gives you the exact details of the expedition

{% tabs %}
{% tab title="Perl" %}
```perl
sub EVENT_SAY{
    if($status > 200) {
		$ReqPlayer = 1;
	} else {
		$ReqPlayer = 4;
	}
    @AdvInfo = plugin::LoadExpeditionInfo2();
	plugin::CheckForStaleInstances();
    if($AdvInfo[0] > 0) {
		plugin::DisplayInstanceQueue($AdvInfo[0]);
	} else {
        plugin::InitInstanceQueue(
			"Velketors Assignment", #Instance Identifier
            "Small Raid", #Description of Adventure (Ex: Group)
            24, #Number of Players
            707, #Task ID Association
            "Velketors Assignment", #Description of Adventure
            7200, #Duration Timer (Seconds)
            0, #Version
            "velketor", #ZoneSN
            -65, #Instance Destination X
            581, #Instance Destination Y
            -152, #Instance Destination Z
            191, #Instance Destination H
            50, #Required Average Level
            $ReqPlayer, #Minimum # of Players
            1, #Is Shared Task (0/1)
            86400, #Lockout Duration
            0, #:::  Boot on completion
            17, # X Compass Loc
            79, # Y Compass Loc
            3, # Z Compass Loc
        );
    }
}
```
{% endtab %}
{% endtabs %}

![](http://wiki.eqemulator.org/l/wa/images/expedition_example/Expedition_ex_1.png)![](http://wiki.eqemulator.org/l/wa/images/expedition_example/Expedition_ex_2.png)

* When you hail the NPC again, since you have an adventure you will then trigger plugin::DisplayInstanceQueue, this will bring up the window that will queue you to go into the instance.

![](http://wiki.eqemulator.org/l/wa/images/expedition_example/Expedition_ex_3.png)

![](http://wiki.eqemulator.org/l/wa/images/expedition_example/Expedition_ex_4.png)

* At this point we've entered a 'Version 0' of Velketor which is our own private instance/expedition
* If you have the Shared Task set to 1 on the Initialize plugin when you started the expedition, all of your players will be synchronized, it doesn't matter if they are in different zones or not
  * If you have 40+ players in an instance, they will all recieve the update

![](http://wiki.eqemulator.org/l/wa/images/expedition_example/Expedition_ex_5.png)

* To speed things up, I have updated my task and got a task completion and an Expedition lockout for 2 hours
  * If I had 'Boot on Completion' set to 1, I would have been booted regardless of whether I had things to do in the instance or not
* If I were to go back to Nexus where the NPC was to give me the task, if I or someone else had a lockout for the identifier 'Velketors Assignment', then I would get a message such as:

![](http://wiki.eqemulator.org/l/wa/images/expedition_example/Expedition_ex_6.png)

