---
title: The AVpos Notecard
keywords: AVsitter2
sidebar: avsitter2_sidebar
permalink: avsitter2_avpos.html
folder: avsitter2
---

## The AVpos Notecard

Nearly every feature of AVsitter can be controlled by editing the AVpos notecard. It defines everything about each SITTERs menu and poses. Much more is possible when you learn to manually write and edit the notecard yourself, rather than using only the [NEW] menu as described in the [Setup](/avsitter2_home.html#setup) section.

{% include note.html content="Your AVpos notecard should always be left as 'full perm', otherwise scripts can not read the notecard with the next owner." %}

### Basic Notecard

If we want to quickly write a notecard for one avatar, with a choice of two poses, where our animation files are called "animation1" and "animation2" and we want to name the poses "Sit1" and "Sit2". We would simply type the following into the AVpos notecard:

```
POSE Sit1|animation1
POSE Sit2|animation2
```

After you adjust and [SAVE] each of the poses and [DUMP] the settings, it would look like this: 

```
POSE Sit1|animation1
POSE Sit2|animation2
{Sit1}<0.000000, 0.000000, 1.000000><0.000000, 0.000000, 0.000000>
{Sit2}<0.000000, 0.000000, 1.000000><0.000000, 0.000000, 0.000000>
```

Note that position settings for the poses will be added by the script after you adjust, [SAVE] and [DUMP] your settings.

## Notecard Commands

This section outlines each of the notecard commands you can use.

{% include important.html content="Make sure to see the next section that shows [notecard examples](/avsitter2_avpos.html#example-notecards) and examine the contents of the Examples [BOX]." %}

### POSE
Use the POSE command to add an animation to the menu. The format is:

    POSE <menu_name>|<animation_filename>

i.e.

    POSE Sit1|animation1

{% include note.html content="[Internal SL animations](http://wiki.secondlife.com/wiki/Internal_Animations) can be used in AVsitter without the animation file existing in the furniture." %}

### SYNC
Use the SYNC command for couple/group animations (e.g. cuddles). When a SYNC animation is played it will play all SYNC poses of the same &lt;menu_name&gt; in all SITTERs within the prim. Usually you would add a SYNC of the same name to each SITTER, using different animations for each SITTER (e.g. Female in *first* SITTER, male in *second* SITTER). The format is: 

    SYNC <menu_name>|<animation_filename>

i.e.

    SYNC Cuddle|hug_female

### TOMENU
This creates a button that leads to a submenu. You will need to have a corresponding MENU line. The format is: 

    TOMENU <menu_name>

i.e.

    TOMENU SITS

### MENU
Begins a submenu. All POSE, SYNC, TOMENU and BUTTON commands that come under a MENU line will be placed in the submenu. You must use a TOMENU command somewhere higher up in the notecard to be able to access the submenu. The format is: 

    MENU <menu_name>

i.e.

    MENU SITS

{% include note.html content="To hide poses from the menu (e.g. because they are triggered by a sequence or script and you don't want them to appear individually), place them under a MENU line that has no corresponding TOMENU line (e.g. [MENU HIDDEN](/avsitter2_sequence.html#hiding-poses))." %}

### BUTTON
This creates a button that can be used for customization of your creations, so users can do more than just choose animations with your menus. When selected by an avatar, a button will send a "link message" that can be received by your own scripts. The format is: 

    BUTTON <menu_name>|<custom_integer>|<custom_string>|<custom_key>


- If &lt;custom_string&gt; is empty then &lt;menu_name&gt; will be used as the string.
- If &lt;custom_integer&gt; is empty then 90200 will be used (90200 is used specifically by the [AVprop plugin](/avsitter2_prop.html)).
- If &lt;custom_integer&gt; is set to [90005](/avsitter2_scripting.html#message-90005) then the menu will be returned automatically.
- If &lt;custom_key&gt; is empty then the avatar's UUID will be used as the key. If a different avatar is controlling the menu with [AVcontrol](/avsitter2_control.html) then the key will include the controller and sitter UUIDs, separated by the pipe (`|`) character.
- Two special values have been added for &lt;custom_key&gt;: `<C>` and `<S>`, which will be replaced with CONTROLLER and SITTER respectively. This is to avoid issues with generic scripts that respond to a link message without being specifically designed for AVsitter, because they don't expect the extra UUID.
- If &lt;menu_name&gt; is empty, then an empty button will be created.

e.g.

    BUTTON Press Me|99

Will send a link message with integer 99, string "Press Me" and the avatar's UUID.

Same as: `llMessageLinked(LINK_SET,99,"Press Me",<avatar_uuid>);`

e.g.

    BUTTON Press Me|90005
Using 90005 will also return the menu to the avatar who pressed the button.

e.g.

    BUTTON Press Me|99|Hello

Will send a link message with integer 99, string "Hello" and the avatar's UUID.

Same as: `llMessageLinked(LINK_SET,99,"Hello",<avatar_uuid>);`

e.g.

    BUTTON Press Me|90030|0|1

Will send a link message with integer [90030](/avsitter2_scripting.html#message-90030), string "0" and key "1".

Same as: `llMessageLinked(LINK_SET,90030,"0","1");`

e.g.

    BUTTON Press Me
    
Will send a link message with integer [90200](/avsitter2_prop.html#message-90200--90220), string "Press Me" and the avatar's UUID.

Same as: `llMessageLinked(LINK_SET,90200,"Press Me",<avatar_uuid>);`

<div class="alert alert-info" role="alert"><i class="fa fa-info-circle"></i>
<b>Note:</b> If you want to replace the system's functionality while keeping the default button label, it's possible to use the zero-width space Unicode character `U+200B` to make it different to the script but identical visually. You can copy/paste that character from here: <code>(​)</code>.
<br />
For example:

<pre>
BUTTON [SWAP]​|99
</pre>

places a button whose label is identical to the system [SWAP] label, but it will send a link message with integer 99. Our custom script would react to this.
</div>
### TEXT
Placed once at the top of the notecard, this will add a line of custom text to your menu. The format is: 

    TEXT <custom_text>

i.e.

    TEXT Welcome to my creation!

You can also include "\n" to start a new line. 

i.e.

    TEXT First Line!\nSecond Line!

### MTYPE
Placed once at the top of the notecard, this controls the "menu type" for all SITTERs. Allows various menu options.

    MTYPE 0

The default. Gives the menu to the sitting avatar when they sit and also when they touch the furniture.

    MTYPE 1

Gives the menu to the sitting avatar only when they touch the furniture. The menu returns as soon as a pose is selected.

    MTYPE 2

Same as MTYPE 1, except the menu does not automatically return when a pose is selected.

    MTYPE 3

With MTYPE 3 the menu is completely switched off and cannot be accessed (except via [link message 90005](/avsitter2_scripting.html#message-90005) or [[AV]root script](/avsitter2_utilities.html#avroot-script) or [[AV]root-security](/avsitter2_utilities.html#avroot-security-script)). You might want this if you have only one pose in the furniture, and don't want a menu.

    MTYPE 4

Same as MTYPE 3, except the menu does not automatically return when a pose is selected.

{% include important.html content="Please note that MTYPE will be ignored when using the [AVcontrol&trade;](/avsitter2_control.html) plugin." %}

### ETYPE
Placed once at the top of the notecard, this controls the "exit type" for all SITTERs. Controls SYNC pose behavior when another pose is played in the same prim. NOTE: does not cancel a SYNC if an avatar simply stands up (for that see the [Autoplay script example](/avsitter2_lsl_example_autoplay.html)).

    ETYPE 0

Switches off ETYPE. i.e. will not return avatars to the first pose in their menu, even if SYNC that excludes them is played in the prim.

    ETYPE 1

The default. Avatars in a SYNC return to the first pose in their menu if someone in the SYNC plays a pose that doesn't include them.

    ETYPE 2

Avatars in a SYNC will be "unseated" if a pose that does not include them is played in the prim.

### SITTER
Begins the menu section for each avatar. The number of SITTER sections should match the number of [AV]sit (A+B) pairs of scripts you have in the prim. SITTER numbering starts at 0. A notecard that contains the info for 3 sitters would have 3 SITTER sections.

e.g.

```
SITTER 0
POSE Sit1|animation1
...

SITTER 1
POSE Sit1|animation1
...

SITTER 2
POSE Sit1|animation1
...
```

Each SITTER section must contain the entire menu for one sitting location.

You may also name each SITTER by including your own text. This text will be shown in the menu dialog, and in the select menu as the button for the SITTER if you are using the [[AV]select script](/avsitter2_utilities.html#avselect-script).

e.g.

```
SITTER 0|Female
POSE Sit1|animation1
...

SITTER 1|Male
POSE Sit1|animation1
...
```


### SET
Placed once at the top of the notecard, this assigns a SET # to all SITTERs. Use only if you need to [assign SitTargets](/avsitter2_sittargets.html).

i.e.

    SET 0

### SELECT
Placed once at the top of the notecard, this controls menu behavior when using the [[AV]select script](/avsitter2_utilities.html#avselect-script).

    SELECT 0

The default. The [[AV]select](/avsitter2_utilities.html#avselect-script) menu shows a disabled symbol (<span style="font-size:150%;">&oslash;</span>) for an occupied seat. The symbol is shown only while solo POSE is being played and not during a SYNC.

    SELECT 1

No disabled symbol will be shown in the [[AV]select](/avsitter2_utilities.html#avselect-script) menu and avatars will always be able to swap into an occupied seat.

    SELECT 2

The disabled symbol (<span style="font-size:150%;">&oslash;</span>) will always be shown for an occupied seat.

### SWAP
Placed once at the top of the notecard, enables/disables the [SWAP] buttons in the menu.

    SWAP 0

Disables [SWAP] in the menu. (note: you can still add your own custom swaps using [link message 90030](/avsitter2_scripting.html#message-90030)).

    SWAP 1

Adds [SWAP] button at the top level of the menu. [SWAP] is only available when there are multiple SITTERs in the prim.

    SWAP 2

The default. Adds [SWAP] in all submenus, not just the top level of the menu.

{% include important.html content="When playing a POSE, [SWAP] will move the avatar to the first *unoccupied* SITTER (if available)." %}

{% include important.html content="When playing a SYNC, [SWAP] will exchange places with the first *occupied* SITTER (if available)." %}

{% include note.html content="You can override SWAP 0 or SWAP 1 and make [SWAP] appear for a specific submenu (see [here](http://avsitter.com/qa/652))." %}

{% include warning.html content="The optional [[AV]select script](/avsitter2_utilities.html#avselect-script) completely replaces the normal [SWAP] buttons." %}

### ADJUST
Placed once at the top of the notecard, allows addition of custom buttons to the [ADJUST] menu.  When selected by an avatar, the button will send a "link message" that can be received by your own scripts. The format is:

    ADJUST <button_name>|<custom_integer>|<button_name>|<custom_integer> ...

The link message will send the &lt;button_name&gt;, &lt;custom_integer&gt;, and the UUID of the avatar, i.e.

    ADJUST [COLOR]|200|[TEXTURE]|300

Will add the buttons [COLOR] and [TEXTURE] to the [ADJUST] menu.

The UUID of the avatar is also sent. When a different avatar is controlling the menu with [AVcontrol](/avsitter2_control.html), then [ADJUST] sends the controller and sitter UUIDs, separated by the pipe (`|`) character.

To override this and provide compatibility with generic scripts that respond to link messages, see [AMENU](#amenu).

### AMENU
Placed once at the top of the notecard, enables and disables the [ADJUST] menu.

    AMENU 0

Removes [ADJUST] completely from the menu.

    AMENU 1

Adds [ADJUST] button only at the top level of the menu.

    AMENU 2

The default. Adds [ADJUST] in all submenus, not just the top level of the menu.

    AMENU 4

Same as `AMENU 0`, but custom buttons under the [ADJUST] menu will not send the second UUID (see [ADJUST](#adjust))

    AMENU 5

Same as `AMENU 1`, but custom buttons under the [ADJUST] menu will not send the second UUID (see [ADJUST](#adjust))

    AMENU 6

Same as `AMENU 2`, but custom buttons under the [ADJUST] menu will not send the second UUID (see [ADJUST](#adjust))

(As we can see, what we're doing is adding 4 when we don't want to send the second UUID.)

{% include note.html content="You can override AMENU 0 or AMENU 1 and make [ADJUST] appear for a specific submenu (see [here](http://avsitter.com/qa/652))." %}

### SEQUENCE
Creates a button that starts a sequence specified in the [AV]sequence_settings notecard. See [sequence instructions](/avsitter2_sequence.html) for details. e.g.

    SEQUENCE Scene1

## Example Notecards

Following are some example notecards, to help with understanding the menu structure. The position/rotation data lines have been omitted.  

### One SITTER
A notecard for one SITTER, and a choice of two poses.

```
POSE Sit1|animation1
POSE Sit2|animation2
```

### Two SITTERs
A notecard for two SITTERs, and a choice of two poses each.

```
SITTER 0
POSE Sit1|animation1
POSE Sit2|animation2

SITTER 1
POSE Sit1|animation1
POSE Sit2|animation2
```

### Three SITTERs
A notecard for three SITTERs, with singles poses.

```
SITTER 0
POSE Sit1|animation1
POSE Sit2|animation2

SITTER 1
POSE Sit1|animation1
POSE Sit2|animation2

SITTER 2
POSE Sit1|animation1
POSE Sit2|animation2
```

### Two SITTERs with Couples
A notecard for two SITTERs, with singles and couples poses.

```
SITTER 0
POSE Sit1|animation1
POSE Sit2|animation2
SYNC Couples1|hug_Female
SYNC Couples2|kiss_Female

SITTER 1
POSE Sit1|animation1
POSE Sit2|animation2
SYNC Couples1|hug_Male
SYNC Couples2|kiss_Male
```

### One SITTER with Submenus
An example of submenus "Sitting" and "Laying".

```
TOMENU Sitting
TOMENU Laying

MENU Sitting
POSE Sit1|animation1
POSE Sit2|animation2

MENU Laying
POSE Lay1|animation3
POSE Lay2|animation4
```

### Two SITTERs with Submenus
Multiple submenus in each SITTER. Note the "Laying" and "Kissing" submenus in each SITTER are within the "Couples" submenu.

```
SITTER 0
TOMENU Singles
TOMENU Couples

MENU Singles
POSE Sit1|animation1
POSE Sit2|animation2

MENU Couples
TOMENU Laying
TOMENU Kissing

MENU Laying
SYNC Lay1|couples1_Female
SYNC Lay2|couples2_Female
SYNC Lay3|couples3_Female

MENU Kissing
SYNC Kiss1|couples4_Female
SYNC Kiss2|couples5_Female
SYNC Kiss3|couples6_Female

SITTER 1
TOMENU Singles
TOMENU Couples

MENU Singles
POSE Sit1|animation1
POSE Sit2|animation2

MENU Couples
TOMENU Laying
TOMENU Kissing

MENU Laying
SYNC Lay1|couples1_Male
SYNC Lay2|couples2_Male
SYNC Lay3|couples3_Male

MENU Kissing
SYNC Kiss1|couples4_Male
SYNC Kiss2|couples5_Male
SYNC Kiss3|couples6_Male
```

{% include important.html content="For further notecard examples, see the notecards inside the examples provided to you in the AVsitter Examples [BOX]." %}

## "Built-In" animation sequence

You can play animations in a series simply by adding extra animations to the [POSE](/avsitter2_avpos.html#pose) (or [SYNC](/avsitter2_avpos.html#sync)) commands. The animations all share the same position/rotation in the notecard, therefore they *must* be designed to be played together. This can be a continuous scene OR simply regular looped animations that were made as a sequence compatible set (all using use the same position/rotation).

The format for the notecard is as follows:

    POSE <menu_name>|<animation>|<duration>|<animation>|<duration>|<animation>|<duration> ...

or

    SYNC <menu_name>|<animation>|<duration>|<animation>|<duration>|<animation>|<duration> ...

e.g.

    POSE Solo-SEQ|anim1|30|anim2|30|anim3|30
    
When "Solo-SEQ" is selected, the animations will cycle between anim1, anim2 and anim3, playing each for 30 seconds.

Usually a sequence will loop, but if a dash ( - ) is entered instead of a duration then the sequence will stop after playing. e.g.

    POSE Solo-SEQ|anim1|30|anim2|-

{% include important.html content="Be sure to examine the sequence furniture examples provided in the AVsitter Examples [BOX]." %}

{% include important.html content="For an alternate sequence method, see the [AVsequence&trade;](/avsitter2_sequence.html) script." %}

## Auto-assign by gender
Determining the gender of an avatar's shape is [now possible](http://wiki.secondlife.com/wiki/OBJECT_BODY_SHAPE_TYPE), and can be used for automatic sitter and default pose assignment in AVsitter2. The gender of an avatar's shape can be set from the Appearance Editor in the SL viewer.  

### SITTER assignment
You can designate a [SITTER](/avsitter2_avpos.html#sitter) for male/female shaped avatars by adding an "M" or "F" after the sitter name. When an avatar sits, they will be assigned to the first unoccupied sitter that matches the gender of their shape, if available. e.g:

```
SITTER 0|Female seat|F
...

SITTER 1|Male seat|M
...
```

If the seat is not gender specific, then don't assign a gender. e.g:  

```
SITTER 2|Friend seat
...
```

{% include important.html content="SITTER assignment will not work in cases where there are [SET](/avsitter2_sittargets.html) defined. Support for this may be added in future." %}

### Pose assignment
Normally, the default pose to play will be the first in the sitter's menu. However, you can specify a different [POSE](/avsitter2_avpos.html#pose) or [SYNC](/avsitter2_avpos.html#sync) as the default for male/female shaped avatars by adding an "M" or "F" after the animation file name. e.g:

```
POSE SitF|Sit1|M
POSE SitM|Sit2|F
```

## Variable speed animations

You can include animations of variable speed by naming them with + or - at the end of the file name and including them in the furniture. These files will be used in place of the default when the speed setting is changed by use of << Softer & Harder >> buttons. 

e.g. if you have a POSE/SYNC as follows:

    SYNC Walking|Walk01

Then you can optionally include the animation files Walk01- (slower version) & Walk01+ (faster version) in addition to the Walk01 animation. Note, there should be no space between the animation name and the +/-.

The << Softer & Harder >> buttons will only be shown in a submenu if &#124;V is added to the MENU line. e.g.

    MENU Workout|V

Pressing the << Softer & Harder >> buttons will change the speed to the slower/faster animations. The speed will remain set until changed or until all avatars stand up from the furniture.


## Extra notecard commands
Some additional notecard commands exist _([read here for more information](avsitter2_SpecialCommands_AVpos.html))_:

- [HELPER](/avsitter2_SpecialCommands_AVpos.html#helper) - use the AVsitter1 style helper system, where you sit on the helper sticks.
- [KFM](/avsitter2_SpecialCommands_AVpos.html#kfm) - if the object uses [llSetKeyframedMotion()](http://wiki.secondlife.com/wiki/LlSetKeyframedMotion).
- [LROT](/avsitter2_SpecialCommands_AVpos.html#lrot) - positioning buttons to work relative to the local rotation of the root prim, instead of global co-ordinates.
- [WARN](/avsitter2_SpecialCommands_AVpos.html#warn) - disable the warning when there aren't enough prims for all sitters or checks for prop permissions.
- DFLT 0 - don't revert to the default pose when all avatars stand (unless the last pose was a SYNC pose).
- NOWIPE - tells the scripts not to wipe sittargets in other prims (use only if you have a good reason as you may end up with prims that have unnecessary SitTargets).

{% include important.html content="Extra commands are not part of settings [DUMP] so you would need to remember to leave them at the top of your notecard." %}

{% include links.html %}
