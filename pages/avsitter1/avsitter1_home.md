---
title: AVsitter1 Instructions
keywords: AVsitter1
sidebar: avsitter1_sidebar
toc: true
permalink: avsitter1_home.html
folder: avsitter1
---

{% include important.html content="AVsitter1 has been superceded by AVsitter2 but may still be useful in cases where a single script is preferred, and may also be a candidate for updating to accommodate additional functionality from AVsitter2." %}


## VIDEOS

<b>BASIC CHAIR SETUP VIDEO</b>

<iframe height="349" src="http://www.youtube.com/embed/sel5-BuCZOM?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe><br>

<b>COUPLES POSES VIDEO</b>

<iframe height="349" src="http://www.youtube.com/embed/jOMhtJr1KC8?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe><br>

<b>NOTECARD COMMANDS VIDEO</b>

<iframe height="349" src="http://www.youtube.com/embed/TO5rm5J3FdY?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>



## SETUP AND ADJUSTMENT

1. To get started, copy the following into your empty furniture:
- "AVsit" script (one for each avatar you plan to seat)
- "AVpos" notecard
- "AVadjuster" script
- "AVhelper" object
- The animations you plan to use

2. Sit on your furniture and choose "[ADJUST]" from the menu. Then choose "[HELPER]" from the menu. You will be unseated and the "AVhelper" object will appear.

3. Sit on the "AVhelper" and accept the request to animate your avatar. You will then get a menu (if you lose this menu just touch your furniture again to get the menu back).

4. Choose "[NEW]" from the menu, and follow the options to add either a new pose, couples pose, or submenu. If you already have submenus created then simply navigate into them to create new poses or submenus there.

5. After creating a new pose, adjust its position by moving the "AVhelper" with the SL building tools until your avatar is in the correct position. Click "[SAVE]" for each animation you adjust before moving on to the next. In the case you have created a couples pose, two helpers will appear and you can move these together and click "[SWAP]" to switch between the two animations.

6. When you have finished configuring the poses, click "[DUMP]" to output your new pose settings into chat and copy-paste the result into your "AVpos" notecard, replacing the contents of the notecard. <b>IF YOU MISS THIS STEP YOUR CHANGES WILL NOT BE SAVED TO THE NOTECARD!!! ALSO, MAKE SURE ANY TRANSLATORS ARE SWITCHED OFF BEFORE PRESSING [DUMP].</b>

7. Remove the "AVhelper" object and "AVadjuster" script from your furniture before sale as these are "no-transfer" (for convenience, owner can type "/5 cleanup" in chat to delete these). Also, leave your "AVpos" notecards "full-perm" or they will not be able to be read by the script once transferred to a new owner.

## MULTIPLE AVATARS

A basic chair for just one avatar will only need a single "AVsit" script and a single "AVpos" notecard (along with the animations) as described above. Beyond that, setups may involve furniture designed for many avatars to sit, and in such cases there will need to be one "AVsit" script placed in the furniture for each avatar to be seated.

There are two options for sitting multiple avatars that cannot be mixed: "multiple AVsit scripts in one prim" and "1 AVsit script per seat". Either you can put several "AVsit" scripts all in one prim, <u><b>or</b></u> you can place one "AVsit" script into each separate 'seat' of your furniture. <b><u>Unfortunately, you cannot mix these setup styles in the same object.</u></b>

{% include note.html content="When adding more than one 'AVsit' script to a single prim, Second Life should automatically name them sequentially when you drop them in together (e.g. 'AVsit','AVsit 1','AVsit 2', etc.) but please <u><b>make sure it does this correctly, as the names must be sequential.</b></u>" %}

It is also very important you follow the information about the <a href="/avsitter1.html#sittarget-add-script">"SitTarget-Add" Script</a> to ensure you do not get the Second Life error "No room to sit here, try another spot".

When multiple "AVsit" scripts are in the same prim, use only one "AVpos" notecard that includes the information for all sitters. The SITTER command is used within the notecard to separate the info for the menu of each sitter's menu. SITTER 0 on a line by itself will indicate the start of the info for your first seat and SITTER 1 for the second seat, etc. Think of each SITTER section as a notecard in itself, one for each "AVsit" script, that defines the menu for one avatar only.

Several "AVsit" scripts in one prim is best for couples furniture, where scripts in separate prims would be best for a 3-seater lounge, or chairs around a table. The first option allows many avatars to sit on one prim (great for mesh and sculpts), as well as offering the "[SWAP]" option in the menu which is ideal for couples poses. However, only a setup with scripts in separate prims will let avatars choose which 'seat' to sit on when they first click-sit on the furniture. If in doubt, look at the example furniture provided in the AVsitter package and compare.

{% include note.html content="When playing a SYNC pose, [SWAP] will only exchange places with other avatars (if present) and when playing a POSE, [SWAP] will first try to move the avatar only to empty positions." %}

## THE "AVhelper" OBJECT

The "AVhelper" is a pose adjustment tool that will rez from the furniture when you select "[HELPER]" from the menu. It is only available when both the "AVhelper" and "AVadjuster" are in a prim of the furniture. Your avatar can sit on an "AVhelper", and move it around with the SL building tools to get perfect positioning.

In the case you are adjusting a SYNC pose, an "AVhelper" will rez for each animation involved in the selected pose (e.g. two "AVhelper" will rez for a couples pose) and you can select and move them together to keep the animations in alignment with each other. To adjust a couples pose follow the same steps as for regular poses and when you "[SAVE]" it will store the position of both helpers in the memory.

Instead of sitting on an "AVhelper" you can also simply touch it, and AVsitter will use the position of your avatar when the pose is saved. Being able to adjust poses like this without sitting on the "AVhelper" allows you to sit on pose balls (like you'd buy from an animation store) to maintain couples animations' positions in relation to each other when adding them to your furniture.

{% include note.html content="If you are working with the setup of several 'AVsit' in one prim, then you can use '[SWAP]' to adjust the poses in your next 'seat' without getting off the 'AVhelper'." %}

## NOTECARD COMMANDS

An "AVpos" notecard will be needed in all furniture made with AVsitter. It holds the information about your menu and animations.

An example notecard, using two "AVsit" scripts in the same prim may look like this:

```
SITTER 0
BUTTON Press Me!|0
TOMENU SITS
MENU SITS
POSE Sit1|animation1
SYNC Cuddle|hug_female
{Sit1}<0.000000, -0.000050, 0.582960><0.000000, 0.000000, 0.000000>
{Cuddle}<0.000000, -0.000050, 0.538680><0.000000, 0.000000, 0.000000>

SITTER 1
TOMENU SITS
MENU SITS
POSE Sit1|animation1
SYNC Cuddle|hug_male
{Sit1}<1.000000, -0.000050, 0.582960><0.000000, 0.000000, 0.000000>
{Cuddle}<1.000000, -0.000050, 0.538680><0.000000, 0.000000, 0.000000>
````

The following are notecard commands you can use:

<b>POSE</b> - Use this command to add an animation. The format is:

    POSE <name in menu>|<animation file name>

{% include tip.html content="Keeping your animation names and menu names short will conserve script memory!" %}

<b>SYNC</b> - Use this command for couple/group animations (e.g. cuddles, kisses). When a SYNC animation is selected by an avatar it will play all SYNC animations that have the same &lt;name in menu&gt;, even if they have different &lt;animation file names&gt;. The format is:

    SYNC <name in menu>|<animation file name>

<b>TOMENU</b> - This creates a link to a submenu. All MENU commands should have a corresponding TOMENU line above them (unless you want the items in that submenu to be hidden from the menu for some reason). The format is:

    TOMENU <your menu name>

<b>MENU</b> - Begins a submenu. All POSE, SYNC, TOMENU and BUTTON commands that come under the MENU line will be placed in that submenu. The format is:

    MENU <your menu name>

<b>BUTTON</b> - This creates a button that can be used for customization of your creations, so users can do more than just choose animations with your menus. When selected by an avatar, a button will send a "link message" that can be received by your own scripts. The format is:

    BUTTON <name in menu>|<custom integer>

The link message will include the &lt;name in menu&gt;, &lt;custom_integer&gt;, and the UUID of the avatar that pressed the button. See the <a href="http://wiki.secondlife.com/wiki/LSL_Portal">Linden Lab Script Reference</a> for more information on "link messages".

<b>MTYPE 1</b> - With this command, AVsitter will not give the menu automatically each time someone sits and the menu is only given when a sitting avatar clicks (touches) the furniture.

<b>MTYPE 2</b> - With this command, animations are changed by a sitting avatar by clicking (touching) the furniture. AVsitter will not give sitting avatars a menu unless they click and hold the mouse button on the furniture for > 2 seconds. This is the best option for basic chairs, where a menu is not wanted.

<b>MTYPE 3</b> - With this command, the menu cannot be accessed unless using the "Root-Security" script or a link message in a script of your own (see below).

<b>ETYPE 1</b> - With this command, sitters in a SYNC pose will return to the first pose in their menu when another POSE or SYNC is played that does not include them. This can prevent one avatar from remaining in a couples pose when their companion has changed to a singles pose. If you also want to change poses automatically when someone sits or stands you should also include a script such as the <a href="/avsitter1.html#script-examples">"Auto-Play" example</a>.

{% include note.html content="If used, the MTYPE and ETYPE commands only need to be in your AVpos notecard once." %}

<b>LOOP</b> - This is an advanced command which only has any effect with MTYPE2. It causes the animations to cycle back to the first animation or previous LOOP, rather than cycling to the next animation. Used with the "Auto-Play" script example, it allows you to make furniture where couples animations are not available unless the correct number of avatars are sitting.

<b>SITTER</b> - If you are using the setup style where all your "AVsit" scripts are in one prim then the SITTER command is used to separate your notecard sections. The number of SITTER sections will match the number of "AVsit" scripts. The format is:

    SITTER <n>|<optional text>

where &lt;n&gt; matches the numbering of the AVsit scripts.

The numbering starts at 0. For example a notecard that contains the info for 3 sitters would have 3 sections, each beginning with the SITTER command (i.e. "SITTER 0", "SITTER 1" and "SITTER 2"). Each SITTER section must contain all the information for the menu you want for that seat. See the example notecard above, or the example furniture provided with AVsitter.

You may also name a sitter by including your own text for &lt;optional text&gt;. This text will be shown in the top level of the menu when that sitter is selected. If &lt;optional text&gt; is included it will also be used by the <a href="/avsitter1.html#avselect-script">"AVselect" script</a>.

<b>POSITION/ROTATION INFO</b> - Under the notecard commands for each SITTER section are the position and rotation settings for the included poses. You won't have to edit these as they are generated automatically when you adjust and "[SAVE]" the poses.

♦ - When AVsitter outputs your pose adjustments you will see this diamond character. All text on a notecard line before this character is ignored, making it possible to copy-paste chat output to your notecards without having to remove the time and object name from each line.

## POSE MEMORY

Furniture made with AVsitter can remember a large number of custom positions for avatars who use the "[ADJUST]" menu to adjust poses (e.g. for adding a fine adjustment to a couples pose, or just getting more comfortable in the chair). The ADJUST menu is for users of the furniture to make custom adjustments for their specific avatars <u><b>ONLY</b></u>. This ADJUST menu is <u><b>NOT</b></u> for setting the master positions for poses! When memory is full, AVsitter will keep the most recently used custom positions and drop the least used.

## "Root" SCRIPT

If your setup does not include an "AVsit" script inside the root prim of your object then you should include the "Root" script in the root prim. It will allow sitters to touch anywhere on the furniture to get the animation menu, instead of having to click on a specific prim.

## "Root-Security" SCRIPT

If you wish to include an optional security function, place this script in the root prim of your object. If you would otherwise be using the "Root" script, delete it and replace it with this. If you use this script you must add "MTYPE 3" to your AVpos notecard. You also need to add a button to each menu in the form of

    BUTTON [SECURITY]|0

in all SITTER sections of your notecard, so that the owner can change the security level. Security cycles between ALL, GROUP ONLY, and OWNER ONLY. Avatars who do not meet the security level will be unseated.

## "SitTarget-Add" SCRIPT

If you have a setup style of multiple "AVsit" scripts in one prim you should add the "SitTarget-Add" script (found in the AVsitter Utilities [BOX]) to <b>other</b> prims in the object, <b>adding it one per prim only, in a separate prim for every sitter after the first.</b>

e.g. if you have 2 AVsit scripts, then there should be 1 other prim containing the "SitTarget-Add" script, and if there are 3 AVsit scripts then there should be 2 separate prims containing it. <b>The "SitTarget-Add" must go in prims that do not contain the "AVsit" script.</b>

Adding enough sit-targets for all your sitters will prevent the Second Life error message "No room to sit here, try another spot". This is an error that can happen when your furniture is placed inside another prim (e.g. simwide landscape sculpt), so is not always obvious.

Some designers do like to offer 1-prim versions of their furniture but need to be aware of this SL issue. Furniture that uses multiple AVsit scripts in one prim without the "SitTarget-Add" script(s) set correctly will work except when placed within the bounding box of another prim.

{% include note.html content="If you've accidentally added this script to a prim in your furniture which uses the other setup style (one AVsit script per seat) you can use the SitTarget-Remove script in that prim which will remove the unwanted sit-target." %}

## "AVselect" SCRIPT

When using a setup of multiple AVsit scripts in a prim it may be that you would prefer to offer a menu of all the different seats instead of having the usual [SWAP] ability which just moves an avatar to the next seat. The AVselect script provides a way in which avatars can choose their seat from a menu.

Features of the AVselect script:


-  If you want to add this feature to existing furniture simply place the AVselect script in the prim that contains your AVsit scripts. All occurrences of [SWAP] are now changed to say [SELECT] and when an avatar chooses [SELECT] they are taken to a menu of the SITTER sections defined in the notecard.

-  If you have only one pose in a SITTER section (i.e. not a whole menu of poses but just one defined for that SITTER) then the AVsit script will automatically turn off the normal AVsitter menu completely so that only the AVselect menu is ever shown for that sitter. This avoids an empty menu with only one pose to choose from. The AVselect menu is reached by touching the furniture.

-  By default, the AVselect menu entry for a sitting location is taken from the name of the first POSE or SYNC in that sitting location's menu section. However, if you prefer to set a custom name for a sitting location then it can be done by manual addition to any SITTER line in the AVpos notecard as follows:

   ```
   SITTER <sitter number>|<optional text>
   ```
   e.g.

   ```
   SITTER 0|Green Pillow
   ```
-  If a singles POSE is playing, AVselect will show a disabled symbol (ø) in the menu for a seat that is occupied by another avatar. When a couples SYNC pose is playing, AVselect will allow swapping with an occupied seat. You can switch off the disabled symbol by including SELECT 1 anywhere in your AVpos notecard.

Please note that the AVselect script should not be used with the <a href="/avsitter1.html#root-security-script">Root-Security script</a>.

## THE "AVplus" SCRIPT

The "AVplus" script provides AVsitter with an easy to use system for rezzing props, playing sounds, giving items, playing facial expressions, and setting a camera angle in your furniture. "AVplus" is found inside the "AVsitter Utilities [BOX]".

Simply place the "AVplus" script in any prim that contains an "AVsit" script and you will see a new menu option called "[EXTRAS]" when you are sitting on the "AVhelper".

The "[EXTRAS]" menu allows you to add extras for most situations, but does not cover every possibility. If you want to get the most out of "AVplus" (playing multiple facial animations, for example, or giving different items to each avatar in a couples pose) then some editing of the notecard will be required. See the relevant sections below for details. After you have finished adding extras, choose the "[DUMP]" menu command and copy-paste the updated settings to your "AVpos" notecard.  AVplus commands can be in any location in the "AVpos" notecard, but it is suggested you put them at the very end.

Please find a detailed description for each of the AVplus features under the subheadings below.

### REZZING PROPS

To set up an object as a prop, first place the "AVprop" script inside the root prim of your prop (not inside your furniture), then place the object in your furniture. Through the "[EXTRAS]" menu, choose "[PROPS]" and then select your object from the list, and it will rez above the centre of your furniture. Position your prop to the desired location and select "[SAVE]" from the menu. The prop will now rez in the set position each time that pose is played. Props should be COPY permissions, otherwise they will not be able to be rezzed more than once.

{% include note.html content="Only one prop can be rezzed from the same prim at a time, and props can be rezzed a maximum of 10 meters from the centre of the prim." %}

The format for the notecard is:

    PROP <menu name>|<object name>|<position>|<rotation>

&lt;menu name&gt; must match the name of the POSE or SYNC that you want to trigger the prop.

&lt;object name&gt; can be any object in the inventory of the prim (must contain "AVprop" script).

An example that rezzes an object "guitar" when the pose "Sing1" is played would be:

    PROP Sing1|guitar|<1,0,0>|<0,0,0>

Props which are triggered by selecting a pose are automatically removed when another pose is selected from the menu, or when all sitters stand up.

An alternative method of rezzing props is to create a BUTTON in your menu (<a href="/avsitter1.html#notecard-commands">see Notecard Commands section above</a>) and use the special link number 90200 along with the <menu name> of your prop. This will rez the prop with the corresponding &lt;object name&gt; when the BUTTON is pressed. For example:

    BUTTON Rez Guitar|90200

then

    PROP Rez Guitar|guitar|<1,0,0>|<0,0,0>

When the "Rez Guitar" button is pressed, the guitar prop will rez.

Props rezzed using a BUTTON stay rezzed until another prop is rezzed, or until all sitters stand up.

{% include note.html content="To get the &lt;position&gt; and &lt;rotation&gt; for a prop that you want to rez with a BUTTON, you can first create the prop through the [EXTRAS] menu as per normal, then change it in the notecard so it is triggered by the BUTTON you have created instead of a specific pose." %}

If you want to clear props with a BUTTON then simply use link message 90200 to refer to a prop that does not exist. For example:

    BUTTON ClearProps|90200

### PLAYING SOUNDS

Through the "[EXTRAS]" menu, choose "[SOUNDS]" and then select a sound from the list, choose the volume, and loop setting, then select "[OK]". Now the selected sound will play whenever the currently selected pose is played.

The format for the notecard is:

    SOUND <pose name>|<sound>|<loop sound>|<volume>

&lt;pose name&gt; must match the name of the POSE or SYNC that you want to trigger the sound.

&lt;sound&gt; can be any sound in the inventory of the prim (or the UUID of a sound).

&lt;loop sound&gt; can either be 1 or 0 (true or false).

&lt;volume&gt; can be any decimal point number from 0.0 ~ 1.0

### GIVING ITEMS

Through the "[EXTRAS]" menu, choose "[ITEMS]" and then select an object from the list. Now the selected object will be given to an avatar's inventory whenever they play the currently selected pose. Items to be given in this way should be COPY and TRANSFER permissions, otherwise they will not be able to be given to the avatar's inventory.

The format for the notecard is:

    ITEM <menu name>|<object name>|<animation file>

&lt;menu name&gt; must match the name of the POSE or SYNC that you want to trigger the item.

&lt;object name&gt; can be any object in the inventory of the prim.

&lt;animation file&gt; is optional but allows you to specify the animation so to only give an item to one of the avatars in a SYNC pose.

An alternative method of giving items is to create a BUTTON in your menu (<a href="/avsitter1.html#notecard-commands">see Notecard Commands section above</a>) and use the special link number 90045 along with the &lt;menu name&gt; of your item. This will give the item when BUTTON is pressed. For example:

    BUTTON Give Item|90045

then

    ITEM Give Item|Object

A completely alternate method to give items is to use the "Menu Button to Give item" script from the <a href="/avsitter1.html#script-examples">scripting examples</a>.

### FACIAL EXPRESSIONS

Through the "[EXTRAS]" menu, choose "[FACES]" and then select an expression from the list. Now the selected facial expression will be played on an avatar whenever they play the currently selected pose.

The format for the notecard is:

    ANIM <pose name>|<animation sequence>|<animation file>

&lt;pose name&gt; must match the name of the POSE or SYNC that you want to trigger the sequence.

&lt;animation sequence&gt; is a list of animations and times to play them in seconds, separated by a colon (:). If a dash (-) is entered instead of a number, the sequence will stop after playing that animation, otherwise the sequence will loop after reaching the end. The times must be in whole seconds.

&lt;animation file&gt; is optional, but allows you to specify the animation so to only play this sequence on one of the avatars in a SYNC pose.

For example in the following notecard line:

    ANIM Fun1|express_laugh_emote:5:express_tongue_out:1|fun2_f

When the "Fun1" pose is selected from the menu and the animation file played on the avatar is "fun2_f", then AVplus will play the animation "express_laugh_emote" on that avatar, then wait 5 seconds, play "express_tongue_out", then wait 1 second, then start again.

Another example:

    ANIM Sleep1|express_smile:1:express_disdain:1

When the "Sleep1" pose is selected, this alternates between "express_smile" and "express_disdain" every second, and appears to give a smooth continuous facial expression for sleeping, with eyes closed.

Any animation can be specified in these sequences. Also, for the full list of internal SL animations see <a href="http://wiki.secondlife.com/wiki/Internal_Animations">http://wiki.secondlife.com/wiki/Internal_Animations</a>. Internal animations can be used in AVsitter without the animation file existing in the furniture.

The facial expresssions available in SL include:

    express_afraid_emote, express_anger_emote, express_laugh_emote, express_bored_emote, express_cry_emote, express_embarrassed_emote, express_sad_emote, express_toothsmile, express_smile, express_surprise_emote, express_worry_emote, express_repulsed_emote, express_shrug_emote, express_wink_emote, express_disdain, express_frown, express_kiss, express_open_mouth, express_tongue_out

### SETTING THE CAMERA

This feature is useful if you want to force the sitter's viewer camera to a position when they sit. Through the "[EXTRAS]" menu, choose "[CAMERA]" and then select a camera view. Now press "[SET]" and the camera angle will be forced on an avatar whenever they sit on the furniture. For now please use this feature only in one-seater furniture, as there is a LL bug preventing camera settings from working properly with more than one avatar on the furniture (see <a href="https://jira.secondlife.com/browse/SVC-7065">https://jira.secondlife.com/browse/SVC-7065</a>).

## "Notecard-Generator" SCRIPT

A "Notecard-Generator" script is included with AVsitter. When placed into your furniture, this script will output text for a basic notecard (listing all of the poses contained in the furniture) which you can then copy-paste from chat into your notecard, saving the need to manually type animation names (if you are using an especially large number of poses this method may be more efficient than adding one pose at a time via AVsitter's in-built menu-making system).

## "MLP-Converter" SCRIPT

This script is designed to assist you in converting an existing MLP furniture into AVsitter form. When placed inside a prim that contains an MLP setup, the "MLP-Converter" script will read through all notecards in the prim that start with either ".MENUITEMS" or ".POSITIONS", which are the standard names for MLP configuration notecards. It will generate text in local chat that will contain the information for the poses it finds in those notecards, as well as the position/rotation data compatible with AVsitter. The text can then be copy-pasted directly into an "AVpos" notecard. Only poses (including singles and couples/group poses) and prop positions will be converted, the converter does not convert the menu structure or other MLP options. The "MLP-Converter" script will remove itself automatically from the prim's inventory once finished. After conversion, please check and adjust each pose to confirm it is correct as the MLP converter does not account for differences in offsets between MLP versions. Please keep in mind that AVsitter uses a single script and has memory limits (approx 120 animations per sitter if you use short animation names) so not all MLP furniture is suitable for conversion to AVsitter.

## SCRIPTING

{% include warning.html content="Don't use this section without a knowledge of <a href=\"http://wiki.secondlife.com/wiki/LSL_Portal\">LSL scripting</a>. If you do not have a knowledge of scripting then please consult your own scripter." %}

One of the features of AVsitter™ is that it enables creators to control animations with their own scripts through "link messages". With the ability to add custom buttons to menus that send their own link messages, the possibilities for your designs are increased. Please only attempt to use these examples if your knowledge of scripting in Second Life is reasonably good.
Below are listed the various link messages and then a selection of example scripts which use them to work with AVsitter.

### Link messages your scripts can receive from AVsitter:

-  <b>90055</b> - This message is sent when an avatar selects a pose from the menu. It includes the name of the pose being played and the UUID of the avatar.

-  <b>90060</b> - This message is sent when a new sitter sits. It includes the UUID of the avatar.

-  <b>90065</b> - This message is sent when a sitter stands. It includes the UUID of the avatar.

### Link messages your scripts can send to AVsitter:

-  <b>90000</b> - Plays an animation. Sending a link message of 90000 will play the animation of the name you give in the link message in all scripts that have it in their menu. If the animation is a SYNC, you must prefix the name given in the link message with "S:", i.e.

   ```
   llMessageLinked(LINK_SET,90000,"S:Cuddle","");
   ```
-  <b>90005</b> - Give menu. Sending this link message with an avatar key will give the animation menu to that avatar if they are sitting, i.e.

   ```
   llMessageLinked(LINK_SET,90005,"",<AVATAR's UUID>);
   ```
   {% include note.html content="If you are using the MTYPE 3 option then 90005 will not work unless you send an integer greater than 2 in the string component of the link message." %}

-  <b>90200</b> - If the "AVplus" script exists in the prim this link message is sent from, then "AVplus" will attempt to rez a PROP, if one is defined with the same name as the string text sent, i.e.

   ```
   llMessageLinked(LINK_SET,90200,"guitar","");
   ```

## SCRIPT EXAMPLES

See the following pages for AVsitter1 script examples:

- [LSL Examples (Beginner)](avsitter1_lsl_examples_beginner.html)
- [LSL Examples (Advanced)](avsitter1_lsl_examples_advanced.html)

{% include links.html %}
