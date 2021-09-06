---
description: A custom dialogue handler using the in game popup window
---

# DiaWind

## Description

* For as long as I know, NPC to player interaction has involved players and quest saylinks to make it easy. But this can be not very entertaining and very bland to read sometimes.
* This plugin will take a lot of the complexities out of making dialogue in general, make it beautiful and bring life to it
  * Allows syntax for animations such as +wave+
  * Allows syntax for simply colors such as light blue {lb}This is light blue~
  * Allows syntax for many different options listed below
  * Appends the NPC name to the window for dialogue
  * Can use 'Mysterious Voice' if you want to use it for narrator type approaches
  * You can set a popup window timer with =70= seconds
  * Easily add bullets {bullet} or indent {in} or linebreak {linebreak}
* Some people might have thought that using popup windows for NPC interaction would be great, but the syntax is painful to use and it is hard to keep a window formatted nice. This plugin solves all of those issues and goes a step above...
* This plugin can also be used as a drop in replacement for quest::say, see video below:
* This is probably one of the best creations of mine and it took the least amount of time. This system is SUPER easy to use and you don't have to think about doing much when you are creating dialogue.
* It is feature rich, and allows you to highlight keywords in a window and format it nicely rather than trying to remember a bunch of fancy codes.
* It takes ALOT of work out of making dialogue stuff work. The below custom markdown can be used anywhere in the first argument of the plugin, it is designed so that it parses the tags and actually formats the popup window accordingly.

## Markdown

* **{lb}** = Light Blue Color
* **{y}** = Yellow Color
* **{gold}** = Gold Color
* **{g}** = Green Color
* **{r}** = Red Color
* **{gray}** = Gray Color
* **~** = End Color Tag \(\)
* **\[&gt;** = Response Text \(Not Visible\) - This is what the player responds with, for example: \[What else do we need to do?&gt;
* **\[\]** = Response Text \(Visible\) - If a NPC has multiple brackets, it will give the player multiple saylinks to click, if there is just one \[bracket\] inline with the text, the player will respond by clicking 'Yes' on the window
* **+66+** = Animation number - As long as there is a number between two plus signs together, the NPC will perform that animation
* **+Salute+** = Animation phrase - This references 

  * plugin::DoAnim

   - If the data between the two ++'s are a string, it will try to parse it with plugin::DoAnim

* **{bullet}** - Equivalent to a bullet such as the one in this list
* **{in}** - Will indent the text
* **{linebreak}** - Will create a linebreak
* **mysterious** - If the text 'mysterious' is anywhere in the text, it will not show up in the player window, but it will format the window as 'Mysterious Voice tells you'
* **wintype:0/1** - If this is 1 the window will be Yes/No
* **popupid:ID** - If this option is present, it will give the popup window and ID
* **noquotes** - This tells the window to not use any quotes for special formatting at times
* **nosound** - No sound affect will play with the window
* **=Timer=** - If a number is specified between the two ==, it will countdown a timer on the popup window

## Usage

{% tabs %}
{% tab title="Perl" %}
```perl
$client->DialogueWindow("markdown");
$client->DiaWind("markdown"); // alias
```
{% endtab %}

{% tab title="Lua" %}
```lua
e.other:DialogueWindow("markdown");
e.other:DiaWind("markdown"); // alias
```
{% endtab %}
{% endtabs %}

## Examples

{% tabs %}
{% tab title="Perl" %}
The below example makes use of basic color highlighting, animations and responses.

```perl
sub EVENT_SAY {
    if($text=~/hail/i) {
        $client->DiaWind("Ahhh, yes, {gold}$name!~. {lb}Very good work~. You must be [very strong willed] my friend.+bowto+");
    } elsif($text=~/very strong willed/i) {
        $client->DiaWind("Ahhh, yes, you see, there is much to be done and {lb}you've only begun~.
        When you are proving yourself in these {y}halls~ I have been troubled to tell you
        to keep in mind you need to see {gold}Falco~. Don't ask questions.[See Falco?>+nodyes+");
    } elsif($text=~/see falco/i) {
        $client->DiaWind("I just told you {y}$name~, there are no questions.
        {y}Falco~ is a {lb}spirit that exists within this realm but only by fine threads~, he has the information that you need.
        But you must be 'prepared'
 
		Do you understand the words that are coming out of my mouth {y} $name~? [I am prepared> +nodyes+");
    } elsif($text=~/prepared/i) {
        $client->DiaWind("Yes, you must be prepared. I will give you what you need to know.+point+");
        quest::taskselector(158);
    } else {
        $client->DiaWind("I'm sorry $name, but now is not your time +nodyes+");
    }
}
```
{% endtab %}
{% endtabs %}

![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_1.png)![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_2.png)![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_3.png)![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_4.png)

{% tabs %}
{% tab title="Perl" %}
Below is another example of colors, animations and responses.

```perl
sub EVENT_SAY{
    if($text=~/hail/i){               
        $client->DiaWind("Yawwnnn. Your name is {gold}$name~? Hrmm, I just can't {gold}remember anymore...~ {gray}I, I, I, ugh... what was it again...~
        Ah, yes strange one.  You wake me from my {lb}slumber~... wait what was it, {lb}who are you?~  I just want to {lb}remember~ [I can help you remember> +31+");
    } elsif($text=~/help you Remember/i){
        $client->DiaWind("The dreams I {lb}used to have~, they were {y}wondeakkadiusrful~.  {lb}Dreams~ of {gold}mountains and skeletons~ and err...
        fire I..I...{gray}I just don't remember~.  Have you ventured into the {gold}angels tower and slept in their wonderful beds~?
        They are amazing but it has been ages since I was able to {lb}feel those beds~. 
        The {y}angels~ {r}banished me~ from the {lb} tower~ for my deeds, but alas, that is another {y}story~...
        Wait, I have a {y}wonderful idea~! {y}YES~!!! This idea is {lb}amazing~ and perhaps you would like to {lb}help~ me with it!!! [I will help you> +cheer+");
    } elsif($text=~/I will help/i){
        $client->DiaWind("Yes... whoever you are, small being.  {lb}Sleep~ in each of those {lb}wonderful beds~ and fall into the dreams in which I try to remember. 
        Bring me back what you remember of the dreams and help {y}ME~ remember the days when I was able to sleep in those amazing beds, will yeh? 
        So what do you think?  {y}Are you willing to take on this~ {lb}task~? [I will take on this task for you> +shrug+");
    } elsif($text=~/I will take on this task/i){
        $client->DiaWind("{y}Perfect~! Start now small one! I am going to try and sleep on this {gray}horrible bed~... +cheer+");
        quest::taskselector(190);
    }
}
```
{% endtab %}
{% endtabs %}

![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_5.png)![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_6.png)![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_7.png)![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_8.png)

{% tabs %}
{% tab title="Perl" %}
A simple use of Mysterious Voice on enter of an NPC Proximity, message disappears in 5 seconds with =5=.

```perl
sub EVENT_ENTER {
	$client->DiaWind("You can't help but observe that {y}Morell Thule~ is {r}shackled~ by some {g}magic spell~...
	{gray}Has he lost his mind? He never roams the bottom floors of the castle...~
	{gray}Morell never comes down to the bottom of the castle...~ =5= mysterious");
}
```
{% endtab %}
{% endtabs %}

![](http://wiki.eqemulator.org/l/wa/images/DiaWind_Examples/DiaWind_Example_9.png)

{% tabs %}
{% tab title="Perl" %}
An example that uses HTML Tables, bullets and indents.

```perl
mysterious {bullet} Would you like to enter: <br> {in} {bullet} {y}Sanctum Somnium~?<br>
{linebreak}<br>
<table>
	<tr><td>
		<tr><td>{in}</td><td>{gold}Expansion:~      </td><td>Visions of Morell</td>
		<tr><td>{in}</td><td>{gold}Tier:~           </td><td>Pre-Progression</td>
		<tr><td>{in}</td><td>{gold}Level Ranges:~   </td><td>90-190</td>
	</td></tr></table>
{linebreak}<br>
{in} {bullet} This expansion goes into the depths of the story between the {y}Thule Gods~ and their endless quarell over realms after the death of {r}Cazic Thule~
popupid:60 wintype:1 nobracket noquotes
```
{% endtab %}
{% endtabs %}

![](http://i.imgur.com/bN2H4Ft.png)

