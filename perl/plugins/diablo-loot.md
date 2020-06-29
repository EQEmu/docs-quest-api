# Diablo Loot

## Description

* This script is designed to generate thousands of lootdrop entries to be dynamically assigned on top of an NPC's original loot.
* It will go through the entire items table and determine for each item, which loot tables it belongs to
* This script is ran pre-server-up once, or as many times as you wish until you feel like you have your loot the way you want it.
* This script has been designed to be ran as many times as you wish as it will purge all of the created entries each time you run it, only to create loads of new entries based on the new criteria that you have fed it.
* All criteria that this script uses is strictly specified in the table \`cust\_npc\_loot\_scale\` that is shown below
* Script requires Perl DBI - to install:  [Install & Config DBD::mysql](https://metacpan.org/pod/distribution/DBD-mysql/lib/DBD/mysql/INSTALL.pod)
* Run the script in your server directory as 'DiabloLoot.pl'

## The Script

* This script is as is, it is a relatively old script of a few years, it is still is kickass though. Do with it what you want, I've been giving everything else away that I've spent tons of time on...
  * The script for me took an average of 2 minutes to run, this is nothing compared to the old stored procedures I ran 3+ years ago that took 20+ minutes a shot and did things much less efficiently
* Example of how you run the script: **perl DiabloLoot.pl all** - does a complete cycle of the script, deletes old entries and creates all new - **You should probably just run this option if you don't know what you're doing**
  * An example of how it creates entries in the database, it uses a reserved range that is defined by options in the script that I wouldn't recommend changing unless you really know what you are doing
    * 200,000 is the Base Loot table ID
      * A level 1 Trash NPC \(Type 0\) would look like this in the database \(200,001\), Named \(Type 1\) would look like \(201,001\), Raid \(Type 2\) would look like \(202,001\) and so on
      * A level 44 would be Trash \(Type 0\) 200,044 - Named 201,044, Raid 202,044
    * You don't need to know exactly how this works, but know that this could interfere with any loot table ID's you already have so it is a good idea to use a reserved range
* **perl DiabloLoot.pl delete** - would do a simple deletion of created Diablo loot entries \(Given you didn't change script options from when they were created\)
* **perl DiabloLoot.pl create** - Does a create cycle without deleting existing entries

{% tabs %}
{% tab title="Perl" %}
```perl
###########################################################
#::: Akka's Diablo Loot
#::: This script is designed to generate thousands of lootdrop entries to be dynamically assigned on top of an NPC's original loot.
#::: This script is ran pre-server-up once, or as many times as you wish until you feel like you have your loot the way you want it.
#::: This script has been designed to be ran as many times as you wish as it will purge all of the created entries each time you run it, only to create loads of new entries based on the new criteria that you have fed it.
#::: All criteria that this script uses is strictly specified in the table `cust_npc_loot_scale` that is shown below
#::: Example: perl DiabloLoot.pl
###########################################################
 
if(!$ARGV[0]) { print "Usage create - creates entries, delete - deletes entries, all - does a complete cycle"; }
else{
    use DBI;
    use DBD::mysql;
    my $start_run = time();
 
    my $Debug = 1;
     
    my $confile = "eqemu_config.xml"; #default
    open(F, "<$confile") or die "Unable to open config: $confile\n";
    my $indb = 0;
    while(<F>) {
        s/\r//g;
        if(/<database>/i) { $indb = 1; }
        next unless($indb == 1);
        if(/<\/database>/i) { $indb = 0; last; }
        if(/<host>(.*)<\/host>/i) { $host = $1; }
        elsif(/<username>(.*)<\/username>/i) { $user = $1; }
        elsif(/<password>(.*)<\/password>/i) { $pass = $1; }
        elsif(/<db>(.*)<\/db>/i) { $db = $1; }
    }
 
    # PERL DBI CONNECT
    $dsn = "dbi:mysql:$db:localhost:3306";
    if(!$connect){ $connect = DBI->connect($dsn, $user, $pass); }
    if(!$connect2){ $connect2 = DBI->connect($dsn, $user, $pass); }
    #####################################################
 
    $n = 0;
    while($ARGV[$n]){ if($ARGV[$n] eq "debug"){ $Debug = " " ; } else{ $Debug = ""; } $n++; }
 
    #::: Script Options :::#
    $MaxLevel = 110;
    $BaseLoottableID = 200000;
    $BaseLoottableIDAugs = 210000;
    $TypeMultiplier = 1000;
    $GenName = "Akkas_Diablo_Loot";
    $GenNameAugs = "Akkas_Diablo_Loot_Augs";
 
    ####################
     
    ###  Load Loot Definitions into Memory so it can be quickly iterated through
    print "Loading Loot Definitions...";
    $query_handle = $connect->prepare("SELECT level, type, hp_min, hp_max, drop_chance, loottable_multiplier, min_plat, max_plat, aug_hp_min, aug_hp_max, aug_ac_max, aug_drop_chance, aug_drop_multiplier FROM `cust_npc_loot_scale` ORDER BY `type`, `level`"); $query_handle->execute();
    while(@row = $query_handle->fetchrow_array()){ $LootDefs[$row[0]][$row[1]] = [@row]; }
    print " Done\n\n";
     
    if($ARGV[0] eq "delete" || $ARGV[0] eq "all"){
        for($i = 0; $i <= 1; $i++){
            if($i == 0){ $ID = $BaseLoottableID; $LT = "'General Loot'"; }
            elsif($i == 1) { $ID = $BaseLoottableIDAugs; $LT = "'Aug Loot'"; }
            print "Creating Loot Table ID's\n" if $Debug;
            $query = "DELETE FROM `lootdrop_entries` WHERE `lootdrop_id` >= " . $ID . " AND `lootdrop_id` <= " . ($ID + 3000) . ";"; 
            $query_handle = $connect->prepare($query);
            my $row = $query_handle->execute(); if($row eq "0E0"){ $row = 0; }
            print "Purging Diablo lootdrop_entries... " . $LT . " rows affected ". $row . "\n";
             
            $query = "DELETE FROM `lootdrop` WHERE `id` >= " . $ID . " AND `id` <= " . ($ID + 3000) . ";";   
            $query_handle = $connect->prepare($query);
            my $row = $query_handle->execute(); if($row eq "0E0"){ $row = 0; }
            print "Purging Diablo lootdrop... " . $LT . " rows affected ". $row . "\n";
             
            $query = "DELETE FROM `loottable_entries` WHERE `lootdrop_id` >= " . $ID . " AND `lootdrop_id` <= " . ($ID + 3000) . ";";
            $query_handle = $connect->prepare($query);
            my $row = $query_handle->execute(); if($row eq "0E0"){ $row = 0; }
            print "Purging Diablo loottable_entries... " . $LT . " rows affected ". $row . "\n";
             
            $query = "DELETE FROM `loottable` WHERE `id` >= " . $ID . " AND `id` <= " . ($ID + 3000) . ";";  
            $query_handle = $connect->prepare($query);
            my $row = $query_handle->execute(); if($row eq "0E0"){ $row = 0; }
            print "Purging Diablo loottable... " . $LT . " rows affected ". $row . "\n";
             
        }
        if($ARGV[0] eq "delete"){ return; }
    }
 
    if($ARGV[0] eq "create" || $ARGV[0] eq "all"){
        print "Creating Loot Table ID's\n" if $Debug;
        for($t = 0; $t <= 2; $t++){
            for($i = 1; $i < $MaxLevel; $i++){
             
                ### Create General Loot Tables ###
                $ID = ($BaseLoottableID + ($TypeMultiplier * $t) + $i);
                $query_handle = $connect->prepare("REPLACE INTO `loottable` (id, name, mincash, maxcash, avgcoin) VALUES (?, ?, ?, ?, ?)");
                $query_handle->execute($ID, $ID . "_" . $GenName, ($LootDefs[$i][$t][6] * 1000),($LootDefs[$i][$t][7] * 1000), 0);
                $query_handle = $connect->prepare("REPLACE INTO `lootdrop` (id, name) VALUES (?, ?)");
                $query_handle->execute($ID, $ID . "_" . $GenName);
                $query_handle = $connect->prepare("REPLACE INTO `loottable_entries` (loottable_id, lootdrop_id, multiplier, droplimit, mindrop, probability) VALUES (?, ?, ?, ?, ?, ?)");
                $query_handle->execute($ID, $ID, $LootDefs[$i][$t][5], 1, 0, 100);
                #sprint $LootDefs[$i][$t][5] . "\n";
                 
                ### Create Augment Tables ###
                $ID = ($BaseLoottableIDAugs + ($TypeMultiplier * $t) + $i);
                $query_handle = $connect->prepare("REPLACE INTO `loottable` (id, name, mincash, maxcash, avgcoin) VALUES (?, ?, ?, ?, ?)");
                $query_handle->execute($ID, $ID . "_" . $GenNameAugs, 0, 0, 0);
                $query_handle = $connect->prepare("REPLACE INTO `lootdrop` (id, name) VALUES (?, ?)");
                $query_handle->execute($ID, $ID . "_" . $GenNameAugs);
                $query_handle = $connect->prepare("REPLACE INTO `loottable_entries` (loottable_id, lootdrop_id, multiplier, droplimit, mindrop, probability) VALUES (?, ?, ?, ?, ?, ?)");
                $query_handle->execute($ID, $ID, $LootDefs[$i][$t][12], 1, 0, 100);
            }
        }
        if($ARGV[0] eq "create"){ return; }
    }
     
    $query_handle = $connect->prepare("SELECT
        items.id,
        items.minstatus,
        items.`Name`,
        items.augtype,
        items.hp,
        items.mana,
        items.ac,
        items.price,
        items.reclevel,
        items.reqlevel,
        items.itemtype
        FROM
        items
        WHERE hp > 0
        AND augtype = 0
        AND minstatus = 0
        AND hp > " . $LootDefs[1][0][3] . "
        ORDER by hp"); $query_handle->execute();
    print "Generating General Loot... Please wait...\n";
     
    $n = 0;
    while(@row = $query_handle->fetchrow_array()){
        my ($id, $MinStatus, $Name, $AugType, $hp, $mana, $ac, $price, $reclevel, $reqlevel, $itemtype) = ($row[0], $row[1], $row[2], $row[3], $row[4], $row[5], $row[6], $row[7], $row[8],  $row[9], $row[10]);
        print "Loop: $n HP: " . $row[4] . " ID: " .  $row[0] . " NAME: " . $row[2] . " "  . "\n" if $Debug;
         
        $TypeCycle = 0;
        while($TypeCycle <= 2){
            $InRange = 0;
            $LevIter = 1;
            while($LevIter < 250){
                $Mult = 1;
                if($itemtype == 1 || $itemtype == 4 || $itemtype == 35){ $Mult = 1.79 } ### We use a multiplier for 2 handed weapons...
                $HPMIN = $LootDefs[$LevIter][$TypeCycle][2] * $Mult;
                $HPMAX = $LootDefs[$LevIter][$TypeCycle][3] * $Mult;
                if($hp > $HPMIN && $hp < $HPMAX){
                    print "(($BaseLoottableID + ($TypeMultiplier * $TypeCycle)) + $LevIter);\n" if $Debug;
                    $ID = (($BaseLoottableID + ($TypeMultiplier * $TypeCycle)) + $LevIter);
                    if($TypeCycle == 1){ print "INSERTING REG - ITEM ID: " . $id . " HP " . $hp . " "  . $ID . " LVL " . $LevIter . " Type " . $TypeCycle . "\n" if $Debug; }
                    $query_handle2 = $connect2->prepare("INSERT INTO `lootdrop_entries` (lootdrop_id, item_id, item_charges, equip_item, chance, minlevel, maxlevel, multiplier) VALUES (?, ?, ?, ?, ?, ?, ?, ?)");
                    $query_handle2->execute($ID, $id, 1, 1, $LootDefs[$LevIter][$TypeCycle][4], 0, 110, 1);
                    $InRange = 1;
                }
                elsif($InRange == 1){ last; }
                $LevIter++;
            }
            #if($TypeCycle > 0){ print $TypeCycle . "\n"; }
            $TypeCycle++;
        }
        $n++;
    }
     
    print "Items Processed: " . $n . "\n";
     
    ### Process Augment Items ###
    $query_handle = $connect->prepare("SELECT
        items.id,
        items.minstatus,
        items.`Name`,
        items.augtype,
        items.hp,
        items.mana,
        items.ac,
        items.price,
        items.reclevel,
        items.reqlevel
        FROM
        items
        WHERE hp > 0
        AND augtype > 0
        AND minstatus = 0
        ORDER by hp"); $query_handle->execute();
    print "Generating Augments Loot... Please wait...\n";
     
    while(@row = $query_handle->fetchrow_array()){
        my ($id, $MinStatus, $Name, $AugType, $hp, $mana, $ac, $price, $reclevel, $reqlevel) = ($row[0], $row[1], $row[2], $row[3], $row[4], $row[5], $row[6], $row[7], $row[8],  $row[9]);
        print "Loop: $n HP: " . $row[4] . " ID: " .  $row[0] . " NAME: " . $row[2] . " "  . "\n" if $Debug;
        $TypeCycle = 0;
        while($TypeCycle <= 2){
            $InRange = 0;
            $LevIter = 1;
            while($LevIter < 250){
                ### Make sure the definitions fall within the stat ranges specified
                if($hp > $LootDefs[$LevIter][$TypeCycle][8] && $hp < $LootDefs[$LevIter][$TypeCycle][9]){
                    $ID = (($BaseLoottableIDAugs + ($TypeMultiplier * $TypeCycle)) + $LevIter);
                    $query_handle2 = $connect2->prepare("INSERT INTO `lootdrop_entries` (lootdrop_id, item_id, item_charges, equip_item, chance, minlevel, maxlevel, multiplier) VALUES (?, ?, ?, ?, ?, ?, ?, ?)");
                    $query_handle2->execute($ID, $id, 1, 1, $LootDefs[$LevIter][$TypeCycle][11], 0, 110, 1);
                    $InRange = 1;
                }
                elsif($InRange == 1){ last; }
                $LevIter++;
            }
            #if($TypeCycle > 0){ print $TypeCycle . "\n"; }
            $TypeCycle++;
        }
        $n++;
    }
 
    print "\n Loot has been successfully generated\n";
    print "Items Processed: " . $n . "\n";
     
    my $end_run = time();
    my $run_time = $end_run - $start_run;
    print "\n\nJob took $run_time seconds\n";
 
}
```
{% endtab %}
{% endtabs %}

## Assigning Loot In Game

* You will need this **START** and **END** code placed in your **EVENT\_SPAWN** routing in your **global\_npc.pl**, so that when your NPC spawns, the loot table can be added

{% tabs %}
{% tab title="Perl" %}
```perl
sub EVENT_SPAWN{
    #:: START: Akka's Diablo Loot Handler ::#
    $NTYPE = 0; #:: TRASH
    if(substr($npc->GetName(), 0, 1) eq "#" && substr($npc->GetName(), 1, 2) ne "#"){  $NTYPE = 1; } #:: NAMED
    if(substr($npc->GetName(), 0, 2) eq "##" && substr($npc->GetName(), 2, 3) ne "#"){ $NTYPE = 2; } #:: RAID
    $LID = (200000 + ($NTYPE * 1000) + $npc->GetLevel());
    if($npc->GetLoottableID() != $LID){
        $npc->ModifyNPCStat("loottable_id", (210000 + ($NTYPE * 1000) + $npc->GetLevel())); $npc->AddLootTable();
        $npc->ModifyNPCStat("loottable_id", (200000 + ($NTYPE * 1000) + $npc->GetLevel())); $npc->AddLootTable(); 
    }
    #:: END: Akka's Diablo Loot Handler ::#
}
```
{% endtab %}
{% endtabs %}

## The Database Table

* The below table is require for the Perl script to run, this is what feeds it data.
* The keys are level and type, for every level there are 3 row entries, 0, 1, 2 for each type
  * **level** = The level of the npc that these rules are effective for
  * **type** = The NPC Type
    * 0 = Trash
    * 1 = Named \(Identified by one \# in the npc name\)
    * 2 = Raid \(Identified by two \#\# in the npc name\)
  * **hp\_min** = the minimum HP the item must be in order to be inserted into a lootdrop entry
  * **hp\_max** = the maximum HP the item must be in order to be inserted into the lootdrop entry
  * **drop\_chance** = the actual drop chance 1 = 100%, 2 = 200% etc
  * **loottable\_multiplier** = the multiplier, this is rolled against drop\_chance, multiplier gets inserted into the lootdrop
  * **min\_plat** = Minimum platinum that will drop for this level and type
  * **max\_plat** = Maximum platinum that will drop for this level and type
  * **aug\_hp\_min** = Minimum AC the aug item must have to fall into this lootdrop
  * **aug\_hp\_max** = Maximum AC the aug item must have to fall into this lootdrop
  * **aug\_ac\_max** = Maximum AC the aug item must have to fall into this lootdrop
  * **aug\_drop\_multiplier** = Aug drop multiplier, augs fall under their own multiplier

{% tabs %}
{% tab title="Query" %}
```sql
SET FOREIGN_KEY_CHECKS=0;
 
DROP TABLE IF EXISTS `cust_npc_loot_scale`;
CREATE TABLE `cust_npc_loot_scale` (
`level` int(11) NOT NULL DEFAULT '0',
`type` int(11) NOT NULL DEFAULT '0',
`hp_min` int(11) DEFAULT NULL,
`hp_max` int(11) DEFAULT NULL,
`drop_chance` float DEFAULT '0',
`loottable_multiplier` int(11) DEFAULT '1',
`min_plat` int(11) DEFAULT '0',
`max_plat` int(11) DEFAULT '0',
`aug_hp_min` int(11) DEFAULT '0',
`aug_hp_max` int(11) DEFAULT '0',
`aug_ac_max` int(11) DEFAULT '0',
`aug_drop_chance` float DEFAULT '0',
`aug_drop_multiplier` int(11) DEFAULT NULL,
PRIMARY KEY (`level`,`type`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
INSERT INTO `cust_npc_loot_scale` VALUES ('1', '0', '14', '17', '1', '8', '0', '1', '1', '1', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('1', '1', '18', '19', '1', '1', '0', '2', '1', '1', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('1', '2', '20', '23', '1', '2', '1', '2', '1', '1', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('2', '0', '28', '34', '1', '8', '0', '1', '2', '3', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('2', '1', '18', '39', '1', '1', '0', '4', '2', '3', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('2', '2', '40', '47', '1', '2', '1', '12', '2', '3', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('3', '0', '42', '51', '1', '8', '0', '1', '2', '4', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('3', '1', '38', '58', '1', '1', '0', '6', '2', '4', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('3', '2', '59', '70', '1', '2', '1', '22', '2', '4', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('4', '0', '56', '68', '1', '8', '0', '1', '3', '5', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('4', '1', '57', '78', '1', '1', '0', '8', '3', '5', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('4', '2', '79', '94', '1', '2', '1', '32', '3', '5', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('5', '0', '70', '85', '1', '8', '0', '5', '3', '6', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('5', '1', '77', '97', '1', '1', '0', '10', '3', '6', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('5', '2', '99', '117', '1', '2', '1', '42', '3', '6', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('6', '0', '84', '102', '1', '8', '0', '6', '4', '8', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('6', '1', '96', '116', '1', '1', '0', '12', '4', '8', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('6', '2', '119', '141', '1', '2', '1', '52', '4', '8', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('7', '0', '98', '119', '1', '8', '1', '7', '5', '9', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('7', '1', '115', '136', '1', '1', '1', '14', '5', '9', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('7', '2', '139', '164', '1', '2', '1', '62', '5', '9', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('8', '0', '112', '136', '1', '8', '1', '8', '5', '10', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('8', '1', '142', '155', '1', '1', '1', '16', '5', '10', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('8', '2', '158', '187', '1', '2', '1', '72', '5', '10', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('9', '0', '126', '153', '1', '8', '1', '9', '6', '11', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('9', '1', '159', '175', '1', '1', '1', '18', '6', '11', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('9', '2', '178', '211', '1', '2', '1', '82', '6', '11', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('10', '0', '140', '170', '1', '8', '1', '10', '7', '13', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('10', '1', '177', '194', '1', '1', '1', '20', '7', '13', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('10', '2', '198', '234', '1', '2', '1', '92', '7', '13', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('11', '0', '154', '187', '1', '7', '1', '11', '7', '14', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('11', '1', '195', '213', '1', '1', '1', '22', '7', '14', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('11', '2', '218', '258', '1', '2', '1', '102', '7', '14', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('12', '0', '168', '204', '1', '7', '1', '12', '8', '15', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('12', '1', '212', '233', '1', '1', '1', '24', '8', '15', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('12', '2', '238', '281', '1', '2', '1', '112', '8', '15', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('13', '0', '182', '221', '1', '7', '1', '13', '8', '16', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('13', '1', '230', '252', '1', '1', '1', '26', '8', '16', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('13', '2', '257', '305', '1', '2', '1', '122', '8', '16', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('14', '0', '196', '238', '1', '7', '1', '14', '9', '18', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('14', '1', '248', '272', '1', '1', '1', '28', '9', '18', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('14', '2', '277', '328', '1', '2', '1', '132', '9', '18', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('15', '0', '210', '255', '1', '5', '1', '15', '10', '19', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('15', '1', '266', '291', '1', '1', '1', '30', '10', '19', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('15', '2', '297', '351', '1', '2', '1', '142', '10', '19', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('16', '0', '224', '272', '1', '5', '1', '16', '10', '20', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('16', '1', '283', '310', '1', '1', '1', '32', '10', '20', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('16', '2', '317', '375', '1', '2', '1', '152', '10', '20', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('17', '0', '238', '289', '1', '5', '1', '17', '11', '21', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('17', '1', '301', '330', '1', '1', '1', '34', '11', '21', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('17', '2', '337', '398', '1', '2', '1', '162', '11', '21', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('18', '0', '252', '306', '1', '5', '1', '18', '12', '23', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('18', '1', '319', '349', '1', '1', '1', '36', '12', '23', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('18', '2', '356', '422', '1', '2', '1', '172', '12', '23', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('19', '0', '266', '323', '1', '5', '1', '19', '12', '24', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('19', '1', '336', '369', '1', '1', '1', '38', '12', '24', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('19', '2', '376', '445', '1', '2', '1', '182', '12', '24', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('20', '0', '280', '340', '1', '5', '1', '20', '13', '25', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('20', '1', '354', '388', '1', '1', '1', '40', '13', '25', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('20', '2', '396', '469', '1', '2', '1', '192', '13', '25', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('21', '0', '294', '357', '1', '5', '1', '21', '13', '26', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('21', '1', '372', '407', '1', '1', '1', '42', '13', '26', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('21', '2', '416', '492', '1', '2', '1', '202', '13', '26', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('22', '0', '308', '374', '1', '4', '1', '22', '14', '28', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('22', '1', '389', '427', '1', '1', '1', '44', '14', '28', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('22', '2', '436', '515', '1', '2', '1', '212', '14', '28', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('23', '0', '322', '391', '1', '4', '1', '23', '15', '29', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('23', '1', '407', '446', '1', '1', '1', '46', '15', '29', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('23', '2', '455', '539', '1', '2', '1', '222', '15', '29', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('24', '0', '336', '408', '1', '4', '1', '24', '15', '30', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('24', '1', '425', '466', '1', '1', '1', '48', '15', '30', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('24', '2', '475', '562', '1', '2', '1', '232', '15', '30', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('25', '0', '350', '425', '1', '4', '1', '25', '16', '31', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('25', '1', '443', '485', '1', '1', '1', '50', '16', '31', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('25', '2', '495', '586', '1', '2', '1', '242', '16', '31', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('26', '0', '364', '442', '1', '3', '1', '26', '17', '33', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('26', '1', '460', '504', '1', '1', '1', '52', '17', '33', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('26', '2', '515', '609', '1', '2', '1', '252', '17', '33', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('27', '0', '378', '459', '1', '3', '1', '27', '17', '34', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('27', '1', '478', '524', '1', '1', '1', '54', '17', '34', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('27', '2', '535', '633', '1', '2', '1', '262', '17', '34', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('28', '0', '392', '476', '1', '3', '1', '28', '18', '35', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('28', '1', '496', '543', '1', '1', '1', '56', '18', '35', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('28', '2', '554', '656', '1', '2', '1', '272', '18', '35', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('29', '0', '406', '493', '1', '3', '1', '29', '18', '36', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('29', '1', '513', '563', '1', '1', '1', '58', '18', '36', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('29', '2', '574', '679', '1', '2', '1', '282', '18', '36', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('30', '0', '420', '510', '1', '3', '1', '30', '19', '38', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('30', '1', '531', '582', '1', '1', '1', '60', '19', '38', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('30', '2', '594', '703', '1', '2', '1', '292', '19', '38', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('31', '0', '434', '527', '1', '3', '1', '31', '20', '39', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('31', '1', '549', '601', '1', '1', '1', '62', '20', '39', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('31', '2', '614', '726', '1', '2', '1', '302', '20', '39', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('32', '0', '448', '544', '1', '3', '1', '32', '20', '40', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('32', '1', '566', '621', '1', '1', '1', '64', '20', '40', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('32', '2', '634', '750', '1', '2', '1', '312', '20', '40', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('33', '0', '462', '561', '1', '3', '1', '33', '21', '41', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('33', '1', '584', '640', '1', '1', '1', '66', '21', '41', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('33', '2', '653', '773', '1', '2', '1', '322', '21', '41', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('34', '0', '476', '578', '1', '3', '1', '34', '22', '43', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('34', '1', '602', '660', '1', '1', '1', '68', '22', '43', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('34', '2', '673', '797', '1', '2', '1', '332', '22', '43', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('35', '0', '490', '595', '1', '3', '1', '35', '22', '44', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('35', '1', '620', '679', '1', '1', '1', '70', '22', '44', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('35', '2', '693', '820', '1', '2', '1', '342', '22', '44', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('36', '0', '504', '612', '1', '3', '1', '36', '23', '45', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('36', '1', '637', '698', '1', '1', '1', '72', '23', '45', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('36', '2', '713', '843', '1', '2', '1', '352', '23', '45', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('37', '0', '518', '629', '1', '3', '1', '37', '23', '46', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('37', '1', '655', '718', '1', '1', '1', '74', '23', '46', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('37', '2', '733', '867', '1', '2', '1', '362', '23', '46', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('38', '0', '532', '646', '1', '3', '1', '38', '24', '48', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('38', '1', '673', '737', '1', '1', '1', '76', '24', '48', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('38', '2', '752', '890', '1', '2', '1', '372', '24', '48', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('39', '0', '546', '663', '1', '3', '1', '39', '25', '49', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('39', '1', '690', '757', '1', '1', '1', '78', '25', '49', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('39', '2', '772', '914', '1', '2', '1', '382', '25', '49', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('40', '0', '560', '680', '1', '3', '1', '40', '25', '50', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('40', '1', '708', '776', '1', '1', '1', '80', '25', '50', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('40', '2', '792', '937', '1', '2', '1', '392', '25', '50', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('41', '0', '574', '697', '1', '2', '1', '41', '26', '51', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('41', '1', '726', '795', '1', '1', '1', '82', '26', '51', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('41', '2', '812', '961', '1', '2', '1', '402', '26', '51', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('42', '0', '588', '714', '1', '2', '1', '42', '27', '53', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('42', '1', '743', '815', '1', '1', '1', '84', '27', '53', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('42', '2', '832', '984', '1', '2', '1', '412', '27', '53', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('43', '0', '602', '731', '1', '2', '1', '43', '27', '54', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('43', '1', '761', '834', '1', '1', '1', '86', '27', '54', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('43', '2', '851', '1007', '1', '2', '1', '422', '27', '54', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('44', '0', '616', '748', '1', '2', '1', '44', '28', '55', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('44', '1', '779', '854', '1', '1', '1', '88', '28', '55', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('44', '2', '871', '1031', '1', '2', '1', '432', '28', '55', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('45', '0', '630', '765', '1', '2', '1', '45', '28', '56', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('45', '1', '797', '873', '1', '1', '1', '90', '28', '56', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('45', '2', '891', '1054', '1', '2', '1', '442', '28', '56', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('46', '0', '644', '782', '1', '2', '1', '46', '29', '58', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('46', '1', '814', '892', '1', '1', '1', '92', '29', '58', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('46', '2', '911', '1078', '1', '2', '1', '452', '29', '58', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('47', '0', '658', '799', '1', '2', '1', '47', '30', '59', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('47', '1', '832', '912', '1', '1', '1', '94', '30', '59', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('47', '2', '931', '1101', '1', '2', '1', '462', '30', '59', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('48', '0', '672', '816', '1', '2', '1', '48', '30', '60', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('48', '1', '850', '931', '1', '1', '1', '96', '30', '60', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('48', '2', '950', '1125', '1', '2', '1', '472', '30', '60', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('49', '0', '686', '833', '1', '2', '1', '49', '31', '61', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('49', '1', '867', '951', '1', '1', '1', '98', '31', '61', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('49', '2', '970', '1148', '1', '2', '1', '482', '31', '61', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('50', '0', '700', '850', '1', '2', '1', '50', '32', '63', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('50', '1', '885', '970', '1', '1', '1', '100', '32', '63', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('50', '2', '990', '1172', '1', '2', '1', '492', '32', '63', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('51', '0', '714', '867', '1', '2', '1', '51', '32', '64', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('51', '1', '903', '989', '1', '1', '1', '102', '32', '64', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('51', '2', '1010', '1195', '1', '2', '1', '502', '32', '64', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('52', '0', '728', '884', '1', '2', '1', '52', '33', '65', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('52', '1', '920', '1009', '1', '1', '1', '104', '33', '65', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('52', '2', '1030', '1218', '1', '2', '1', '512', '33', '65', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('53', '0', '742', '901', '1', '2', '1', '53', '33', '66', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('53', '1', '938', '1028', '1', '1', '1', '106', '33', '66', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('53', '2', '1049', '1242', '1', '2', '1', '522', '33', '66', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('54', '0', '756', '918', '1', '2', '1', '54', '34', '68', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('54', '1', '956', '1048', '1', '1', '1', '108', '34', '68', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('54', '2', '1069', '1265', '1', '2', '1', '532', '34', '68', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('55', '0', '770', '935', '1', '2', '1', '55', '35', '69', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('55', '1', '974', '1067', '1', '1', '1', '110', '35', '69', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('55', '2', '1089', '1289', '1', '2', '1', '542', '35', '69', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('56', '0', '784', '952', '1', '2', '1', '56', '35', '70', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('56', '1', '991', '1086', '1', '1', '1', '112', '35', '70', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('56', '2', '1109', '1312', '1', '2', '1', '552', '35', '70', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('57', '0', '798', '969', '1', '2', '1', '57', '36', '71', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('57', '1', '1009', '1106', '1', '1', '1', '114', '36', '71', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('57', '2', '1129', '1336', '1', '2', '1', '562', '36', '71', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('58', '0', '812', '986', '1', '2', '1', '58', '37', '73', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('58', '1', '1027', '1125', '1', '1', '1', '116', '37', '73', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('58', '2', '1148', '1359', '1', '2', '1', '572', '37', '73', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('59', '0', '826', '1003', '1', '2', '1', '59', '37', '74', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('59', '1', '1044', '1145', '1', '1', '1', '118', '37', '74', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('59', '2', '1168', '1382', '1', '2', '1', '582', '37', '74', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('60', '0', '840', '1020', '1', '2', '1', '60', '38', '75', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('60', '1', '1062', '1164', '1', '1', '1', '120', '38', '75', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('60', '2', '1188', '1406', '1', '2', '1', '592', '38', '75', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('61', '0', '854', '1037', '1', '2', '1', '61', '38', '76', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('61', '1', '1080', '1183', '1', '1', '1', '122', '38', '76', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('61', '2', '1208', '1429', '1', '2', '1', '602', '38', '76', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('62', '0', '868', '1054', '1', '2', '1', '62', '39', '78', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('62', '1', '1097', '1203', '1', '1', '1', '124', '39', '78', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('62', '2', '1228', '1453', '1', '2', '1', '612', '39', '78', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('63', '0', '882', '1071', '1', '2', '1', '63', '40', '79', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('63', '1', '1115', '1222', '1', '1', '1', '126', '40', '79', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('63', '2', '1247', '1476', '1', '2', '1', '622', '40', '79', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('64', '0', '896', '1088', '1', '2', '1', '64', '40', '80', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('64', '1', '1133', '1242', '1', '1', '1', '128', '40', '80', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('64', '2', '1267', '1500', '1', '2', '1', '632', '40', '80', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('65', '0', '910', '1105', '1', '2', '1', '65', '41', '81', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('65', '1', '1151', '1261', '1', '1', '1', '130', '41', '81', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('65', '2', '1287', '1523', '1', '2', '1', '642', '41', '81', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('66', '0', '924', '1122', '1', '2', '1', '66', '42', '83', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('66', '1', '1168', '1280', '1', '1', '1', '132', '42', '83', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('66', '2', '1307', '1546', '1', '2', '1', '652', '42', '83', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('67', '0', '938', '1139', '1', '2', '1', '67', '42', '84', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('67', '1', '1186', '1300', '1', '1', '1', '134', '42', '84', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('67', '2', '1327', '1570', '1', '2', '1', '662', '42', '84', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('68', '0', '952', '1156', '1', '2', '1', '68', '43', '85', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('68', '1', '1204', '1319', '1', '1', '1', '136', '43', '85', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('68', '2', '1346', '1593', '1', '2', '1', '672', '43', '85', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('69', '0', '966', '1173', '1', '2', '1', '69', '43', '86', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('69', '1', '1221', '1339', '1', '1', '1', '138', '43', '86', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('69', '2', '1366', '1617', '1', '2', '1', '682', '43', '86', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('70', '0', '980', '1190', '1', '2', '1', '70', '44', '88', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('70', '1', '1239', '1358', '1', '1', '1', '140', '44', '88', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('70', '2', '1386', '1640', '1', '2', '1', '692', '44', '88', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('71', '0', '994', '1207', '1', '1', '1', '71', '45', '89', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('71', '1', '1257', '1377', '1', '1', '1', '142', '45', '89', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('71', '2', '1406', '1664', '1', '2', '1', '702', '45', '89', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('72', '0', '1008', '1224', '1', '1', '1', '72', '45', '90', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('72', '1', '1274', '1397', '1', '1', '1', '144', '45', '90', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('72', '2', '1426', '1687', '1', '2', '1', '712', '45', '90', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('73', '0', '1022', '1241', '1', '1', '1', '73', '46', '91', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('73', '1', '1292', '1416', '1', '1', '1', '146', '46', '91', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('73', '2', '1445', '1710', '1', '2', '1', '722', '46', '91', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('74', '0', '1036', '1258', '1', '1', '1', '74', '47', '93', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('74', '1', '1310', '1436', '1', '1', '1', '148', '47', '93', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('74', '2', '1465', '1734', '1', '2', '1', '732', '47', '93', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('75', '0', '1050', '1275', '1', '1', '1', '75', '47', '94', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('75', '1', '1328', '1455', '1', '1', '1', '150', '47', '94', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('75', '2', '1485', '1757', '1', '2', '1', '742', '47', '94', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('76', '0', '1064', '1292', '1', '1', '1', '76', '48', '95', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('76', '1', '1345', '1474', '1', '1', '1', '152', '48', '95', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('76', '2', '1505', '1781', '1', '2', '1', '752', '48', '95', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('77', '0', '1078', '1309', '1', '1', '1', '77', '48', '96', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('77', '1', '1363', '1494', '1', '1', '1', '154', '48', '96', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('77', '2', '1525', '1804', '1', '2', '1', '762', '48', '96', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('78', '0', '1092', '1326', '1', '1', '1', '78', '49', '98', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('78', '1', '1381', '1513', '1', '1', '1', '156', '49', '98', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('78', '2', '1544', '1828', '1', '2', '1', '772', '49', '98', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('79', '0', '1106', '1343', '1', '1', '1', '79', '50', '99', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('79', '1', '1398', '1533', '1', '1', '1', '158', '50', '99', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('79', '2', '1564', '1851', '1', '2', '1', '782', '50', '99', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('80', '0', '1120', '1360', '1', '1', '1', '80', '50', '100', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('80', '1', '1416', '1552', '1', '1', '1', '160', '50', '100', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('80', '2', '1584', '1874', '1', '2', '1', '792', '50', '100', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('81', '0', '1134', '1377', '1', '1', '1', '81', '51', '101', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('81', '1', '1434', '1571', '1', '1', '1', '162', '51', '101', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('81', '2', '1604', '1898', '1', '2', '1', '802', '51', '101', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('82', '0', '1148', '1394', '1', '1', '1', '82', '52', '103', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('82', '1', '1451', '1591', '1', '1', '1', '164', '52', '103', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('82', '2', '1624', '1921', '1', '2', '1', '812', '52', '103', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('83', '0', '1162', '1411', '1', '1', '1', '83', '52', '104', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('83', '1', '1469', '1610', '1', '1', '1', '166', '52', '104', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('83', '2', '1643', '1945', '1', '2', '1', '822', '52', '104', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('84', '0', '1176', '1428', '1', '1', '1', '84', '53', '105', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('84', '1', '1487', '1630', '1', '1', '1', '168', '53', '105', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('84', '2', '1663', '1968', '1', '2', '1', '832', '53', '105', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('85', '0', '1190', '1445', '1', '1', '1', '85', '53', '106', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('85', '1', '1505', '1649', '1', '1', '1', '170', '53', '106', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('85', '2', '1683', '1992', '1', '2', '1', '842', '53', '106', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('86', '0', '1204', '1462', '1', '1', '1', '86', '54', '108', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('86', '1', '1522', '1668', '1', '1', '1', '172', '54', '108', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('86', '2', '1703', '2015', '1', '2', '1', '852', '54', '108', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('87', '0', '1218', '1479', '1', '1', '1', '87', '55', '109', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('87', '1', '1540', '1688', '1', '1', '1', '174', '55', '109', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('87', '2', '1723', '2038', '1', '2', '1', '862', '55', '109', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('88', '0', '1232', '1496', '1', '1', '1', '88', '55', '110', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('88', '1', '1558', '1707', '1', '1', '1', '176', '55', '110', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('88', '2', '1742', '2062', '1', '2', '1', '872', '55', '110', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('89', '0', '1246', '1513', '1', '1', '1', '89', '56', '111', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('89', '1', '1575', '1727', '1', '1', '1', '178', '56', '111', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('89', '2', '1762', '2085', '1', '2', '1', '882', '56', '111', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('90', '0', '1260', '1530', '1', '1', '1', '90', '57', '113', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('90', '1', '1593', '1746', '1', '1', '1', '180', '57', '113', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('90', '2', '1782', '2109', '1', '2', '1', '892', '57', '113', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('91', '0', '1274', '1547', '1', '1', '1', '91', '57', '114', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('91', '1', '1611', '1765', '1', '1', '1', '182', '57', '114', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('91', '2', '1802', '2132', '1', '2', '1', '902', '57', '114', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('92', '0', '1288', '1564', '1', '1', '1', '92', '58', '115', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('92', '1', '1628', '1785', '1', '1', '1', '184', '58', '115', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('92', '2', '1822', '2156', '1', '2', '1', '912', '58', '115', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('93', '0', '1302', '1581', '1', '1', '1', '93', '58', '116', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('93', '1', '1646', '1804', '1', '1', '1', '186', '58', '116', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('93', '2', '1841', '2179', '1', '2', '1', '922', '58', '116', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('94', '0', '1316', '1598', '1', '1', '1', '94', '59', '118', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('94', '1', '1664', '1824', '1', '1', '1', '188', '59', '118', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('94', '2', '1861', '2202', '1', '2', '1', '932', '59', '118', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('95', '0', '1330', '1615', '1', '1', '1', '95', '60', '119', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('95', '1', '1682', '1843', '1', '1', '1', '190', '60', '119', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('95', '2', '1881', '2226', '1', '2', '1', '942', '60', '119', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('96', '0', '1344', '1632', '1', '1', '1', '96', '60', '120', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('96', '1', '1699', '1862', '1', '1', '1', '192', '60', '120', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('96', '2', '1901', '2249', '1', '2', '1', '952', '60', '120', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('97', '0', '1358', '1649', '1', '1', '1', '97', '61', '121', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('97', '1', '1717', '1882', '1', '1', '1', '194', '61', '121', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('97', '2', '1921', '2273', '1', '2', '1', '962', '61', '121', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('98', '0', '1372', '1666', '1', '1', '1', '98', '62', '123', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('98', '1', '1735', '1901', '1', '1', '1', '196', '62', '123', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('98', '2', '1940', '2296', '1', '2', '1', '972', '62', '123', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('99', '0', '1386', '1683', '1', '1', '1', '99', '62', '124', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('99', '1', '1752', '1921', '1', '1', '1', '198', '62', '124', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('99', '2', '1960', '2320', '1', '2', '1', '982', '62', '124', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('100', '0', '1400', '1700', '0.1', '1', '1', '100', '63', '125', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('100', '1', '1770', '1940', '1', '1', '1', '200', '65', '130', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('100', '2', '1980', '2343', '1', '2', '1', '992', '65', '130', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('101', '0', '1414', '1717', '0.1', '1', '1', '101', '63', '126', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('101', '1', '1788', '1959', '1', '1', '1', '202', '72', '143', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('101', '2', '2000', '2366', '1', '2', '1', '1002', '72', '143', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('102', '0', '1428', '1734', '0.1', '1', '1', '102', '64', '128', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('102', '1', '1805', '1979', '1', '1', '1', '204', '79', '157', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('102', '2', '2020', '2390', '1', '2', '1', '1012', '79', '157', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('103', '0', '1442', '1751', '0.1', '1', '1', '103', '65', '129', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('103', '1', '1823', '1998', '1', '1', '1', '206', '85', '170', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('103', '2', '2039', '2413', '1', '2', '1', '1022', '85', '170', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('104', '0', '1456', '1768', '0.1', '1', '1', '104', '65', '130', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('104', '1', '1841', '2018', '1', '1', '1', '208', '92', '183', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('104', '2', '2059', '2437', '1', '2', '1', '1032', '92', '183', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('105', '0', '1470', '1785', '0.1', '1', '1', '105', '66', '131', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('105', '1', '1859', '2037', '1', '1', '1', '210', '99', '197', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('105', '2', '2079', '2460', '1', '2', '1', '1042', '99', '197', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('106', '0', '1484', '1802', '0.1', '1', '1', '106', '67', '133', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('106', '1', '1876', '2056', '1', '1', '1', '212', '105', '210', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('106', '2', '2099', '2484', '1', '2', '1', '1052', '105', '210', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('107', '0', '1498', '1819', '0.1', '1', '1', '107', '67', '134', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('107', '1', '1894', '2076', '1', '1', '1', '214', '112', '223', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('107', '2', '2119', '2507', '1', '2', '1', '1062', '112', '223', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('108', '0', '1512', '1836', '0.1', '1', '1', '108', '68', '135', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('108', '1', '1912', '2095', '1', '1', '1', '216', '118', '236', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('108', '2', '2138', '2530', '1', '2', '1', '1072', '118', '236', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('109', '0', '1526', '1853', '0.1', '1', '1', '109', '68', '136', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('109', '1', '1929', '2115', '1', '1', '1', '218', '125', '250', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('109', '2', '2158', '2554', '1', '2', '1', '1082', '125', '250', '0', '5', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('110', '0', '1540', '1870', '0.1', '1', '1', '110', '69', '138', '0', '0.01', '1');
INSERT INTO `cust_npc_loot_scale` VALUES ('110', '1', '1947', '2134', '1', '1', '1', '220', '132', '263', '0', '1', '2');
INSERT INTO `cust_npc_loot_scale` VALUES ('110', '2', '2178', '2577', '1', '2', '1', '1092', '132', '263', '0', '5', '2');
```
{% endtab %}
{% endtabs %}

