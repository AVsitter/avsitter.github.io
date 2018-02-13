---
title: AVprop&trade;
summary: AVprop allows AVsitter&trade; to rez props and can also be used as a standalone prop rezzer in creations without seating. Props are inworld objects rezzed on the land. Props can also become avatar attachments.
keywords: plugin, prop
sidebar: avsitter2_sidebar
permalink: avsitter2_prop.html
folder: avsitter2
---

{% include note.html content="Props are not TEMP_ON_REZ and will count towards land prim limits." %}

{% include tip.html content="For examples that use props, see the AVprop examples in the Plugins Examples [BOX]." %}

{% include important.html content="For answers to some common questions about props please see the [AVsitter Q&A archive.](https://avsitter.com/qa)" %}


## Preparing Prop Objects

Before adding a prop to your project, you'll need to create the prop object:

1. Choose any object you want to use as a prop. e.g. Laptop Computer, Reading Book, Coffee Cup, etc. 
2. Drop the **[AV]object** script into the object's root prim.
3. Repeat for each object you plan to use as a prop.

{% include important.html content="Normal props *must* be COPY-OK for NEXT OWNER." %}

{% include note.html content="If your prop is to be an avatar attachment, also see the [section about avatar attachments](/avsitter2_prop.html#attachment-props)." %}

{% include warning.html content="Remember to use the correct script: [AV]object goes inside your prop objects." %}

## Setting up a Prop with AVsitter&trade;

To add props to your furniture, start with the [normal setup](/avsitter2_home.html#setup) procedure, then:

1. Ensure the [AV]helper and [AV]adjuster are in the prim.
2. Drop the [AV]prop script and your prepared prop objects into the prim.
3. Sit on the prim, then choose a pose from the menu that you want to trigger the prop.
4. Choose [ADJUST] then [HELPER] from the menu, and the [AV]helper stick will rez.
5. Choose [NEW] from the menu, then choose [PROP].
6. Choose your prop object from the menu and the prop object will rez inworld.
7. Move the prop object with the SL building tools to where you want it to rez inworld, then click [SAVE]. Props can rez a maximum of 10 meters from the centre of the prim.
8. Repeat for each prop.
9. When you have finished saving all your props, click [DUMP] to output your settings into chat.
10 .Copy-paste the [DUMP] result into your AVpos notecard, replacing the contents of the notecard.

{% include note.html content="Props are defined separately for each SITTER." %}

{% include warning.html content="Remember to use the correct script: [AV]object goes inside your prop objects, [AV]prop goes inside your furniture." %}

### Props with AVsit Video

<iframe height="349" src="https://www.youtube.com/embed/dt2IcAweM2Y?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>

{% include tip.html content="If English is not your language, the videos have captions for automatic translation." %}

## Setting up a Prop with AVmenu&trade;

With AVmenu&trade; you can create menus in prims that don't have animations. The [AV]menu script can be used in spare prims of furniture or in stand-alone objects that don't have seating (e.g. lazy Susan, kitchen/bar, item dispenser, drinks machine).

{% include important.html content="The [AV]menu script can be used in any prim that does *NOT* include the [AV]sit, [AV]root or [AV]root-security scripts." %}

As with the [AV]sit scripts, [AV]menu is controlled by an AVpos notecard. [AV]menu allows BUTTON, TOMENU, MENU, TEXT and MTYPE 3 from the [Notecard Commands](/avsitter2_avpos.html#notecard-commands) to be used to create menus and also reacts to the [90005 link message](/avsitter2_scripting.html#link-messages-to-send) in the same way as the [AV]sit scripts.

To add props to a prim using [AV]menu:

1. Drop the following into the prim:
  - [AV]menu script
  - [AV]prop script
  - AVpos notecard
  - Your prepared prop objects
2. Touch the prim, choose [OWNER] to enter the owner menu.
3. Choose [NEW] from the menu, then choose your prop object from the menu.
4. The dialog will ask you to name your prop and then the prop object will rez.
5. Move the prop object with the SL building tools to where you want it to rez inworld, then click [SAVE].
    {% include note.html content="Props can be positioned a maximum of 10 meters from the centre of the prim." %}
6. Repeat for each prop.
7. When you have finished saving all your props, click [DUMP] to output your settings into chat.
8. Copy-paste the [DUMP] result into your AVpos notecard, replacing the contents of the notecard.

{% include warning.html content="End-users of objects made with [AV]menu & [AV]prop will see [NEW] and [DUMP] in [AV]menu's [OWNER] menu, unless you set the [AV]prop script to NO-COPY or NO-TRANSFER." %}

### Props with AVmenu Video

<iframe height="349" src="https://www.youtube.com/embed/ynoFR8ZqEyo?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>

{% include tip.html content="If English is not your language, the videos have captions for automatic translation." %}

## Attachment Props
Props can be set to request permission to attach to the avatar after they rez inworld. Even if your prop is an attachment it must rez inworld before it asks the avatar for permisison to attach.

Before you place an attachment prop inside the furniture, you need to attach it and adjust it just like you would if editing prim clothing that you avatar wears. SL automatically remembers the attachment position for an object. When you are happy with the way it's attached, you then detach it and place it in the furniture.

After setting up a prop, you can designate the prop to be an attachment by editing the AVpos notecard and changing its &lt;prop_type&gt; to PROP1 or PROP2 as described in the [Notecard Commands section](/avsitter2_prop.html#notecard-commands).

{% include important.html content="Attachment props *must* be COPY-OK & TRANSFER-OK for NEXT OWNER." %}

## Notecard Commands
You can edit the AVpos notecard to change how props will behave.

The format for the notecard is:

    <prop_type> <trigger_name>|<prop_object>|<prop_group>|<position>|<rotation>|<attachment_point>

&lt;prop_type&gt; can be any of:

- **PROP** is a regular prop.
- **PROP1** requests permission to attach to the avatar as soon as it is rezzed.
- **PROP2** rezzes as a regular prop and requests permission to attach to an avatar when touched.
- **PROP3** is a special type used only by the [shared prop script examples](/avsitter2_lsl_examples_avprop.html).
</ul>

{% include note.html content="If you want to change a prop's &lt;prop_type&gt; then you'll need to edit the notecard." %}

&lt;trigger_name&gt; must match the menu name of the pose (or BUTTON) that you want to trigger the prop.

&lt;prop_group&gt; assigns the prop to a user-defined group. A prop will derez when a new prop is rezzed that has the same prop group. This is relevant when Rezzing/De-Rezzing props [by BUTTON](/avsitter2_prop.html#rezzing-props-by-button) or [by scripting](/avsitter2_prop.html#lsl-scripting).

&lt;attachment_point&gt; defines the attach point to use. Only needed when &lt;prop_type&gt; is set to PROP1 or PROP2.

Possible values:

    chest, head, left shoulder, right shoulder, left hand, right hand, left foot, right foot, back, pelvis, mouth, chin, left ear, right ear, left eye, right eye, nose, right upper arm, right lower arm, left upper arm, left lower arm, right hip, right upper leg, right lower leg, left hip, left upper leg, left lower leg, stomach, left pectoral, right pectoral, HUD center 2, HUD top right, HUD top, HUD top left, HUD center, HUD bottom left, HUD bottom, HUD bottom right, neck, avatar center

## Experience Keys
Second Life has now enabled 'experiences' which will allow automatic attachments (without need for any permission request).

{% include important.html content="If you compiled [AV]object from GitHub yourself, this section doesn't apply, as the script won't have the AVsitter experience by Code Violet." %}

For automatic attachments to work, Users will need to enable the experience <ins>'AVsitter'</ins> (created by Code Violet) on their land. An experience may be enabled at the Estate or Parcel level by [adding it to the **'Allowed Experiences'** list](https://avsitter.com/pics/experiences.jpg). For an excellent explanation, [see this video by Froukje Hoorenbeek](https://www.youtube.com/watch?v=3gcy403FtAk). Be sure to choose [the experience created by Code Violet](https://avsitter.com/pics/experiences2.jpg) as anyone could have accidentally created an experience with the same name.

You can find out more about 'experiences' on the [SL blog](https://community.secondlife.com/t5/English-Knowledge-Base/Experiences-in-Second-Life/ta-p/2744686) and in the [SL scripting WIKI](http://wiki.secondlife.com/wiki/Category:Experience_Tools).

{% include important.html content="If users do not enable the <ins>'AVsitter' by Code Violet</ins> experience then each prop will require permission to attach and the owner may receive the message \"To enable auto-attachments, please enable the experience in About Land.\" ([discussion](https://avsitter.com/qa/251/))" %}

## Rezzing Props by BUTTON
If you want a [BUTTON](/avsitter2_avpos.html#button) to trigger a prop, first [create the prop as normal](/avsitter2_prop.html#setting-up-a-prop-with-avsittertrade) so that it rezzes for a pose, then edit the notecard to change the &lt;trigger_name&gt; of the prop to match your BUTTON. Alternately, add the PROP line manually to your notecard. e.g.

    BUTTON Rez Guitar
    ...
    PROP Rez Guitar|guitar|G1|<0.000000, 0.000000, 1.000000>|<0.000000, 0.000000, 0.000000>

When the "Rez Guitar" button is pressed, the guitar prop object will rez.

If you don't want the menu returned then use the 90220 link message in the BUTTON. e.g.

    BUTTON Rez Guitar|90220

## De-Rezzing Props by BUTTON

If you want a [BUTTON](/avsitter2_avpos.html#button) to clear all props then simply refer to a prop that does not exist. e.g.

    BUTTON [CLEAR]

To make a [BUTTON](/avsitter2_avpos.html#button) to clear props by name then send remprop_&lt;trigger_name&gt; as the button's &lt;custom_string&gt; using integer 90200. e.g.

    BUTTON Clear Fruit|90200|remprop_Fruit

If you want a [BUTTON](/avsitter2_avpos.html#button) to clear all props in one &lt;prop_group&gt; then you can create a blank prop with the same &lt;prop_group&gt;. It's important to leave the &lt;prop_object&gt; for the blank prop empty as in the 'Clear Quilt' example below. e.g.

```
BUTTON Quilt1
BUTTON Quilt2
BUTTON Clear Quilt
...
PROP Quilt1|object1|G1|<0.000004, 0.003191, 0.204285>|<180.000000, 0.000000, 0.000000>|
PROP Quilt2|object2|G1|<0.000004, 0.003191, 0.204285>|<180.000000, 0.000000, 0.000000>|
PROP Clear Quilt||G1
```

## Prop behavior
{% include note.html content="Props triggered by a pose will derez when a new pose is played for the avatar." %}

{% include note.html content="Props triggered by BUTTON or scripting will derez when another prop of same &lt;prop_group&gt; is told to rez." %}

{% include note.html content="Props rezzed from a sitter prim will derez when the avatar stands up or swaps to a new seat." %}

{% include note.html content="Props rezzed from a prim without sit scripts will remain after the avatar stands up." %}

{% include note.html content="Attachment props will automatically detach if a second attachment prop attaches to the same attachment point." %}

{% include important.html content="Attachment props will <i>not</i> create new inventory and will disappear on disconnect." %}

## Example Notecards
Following are some examples of notecard lines and complete notecards relating to AVprop&trade;

### PROP line examples

Rez the book object when the Reading pose is played:  

    PROP Reading|book|G1|<0.000000, 0.000000, 1.000000>|<0.000000, 0.000000, 0.000000>

Attach pen to avatar's right hand when the Writing pose is played:

    PROP1 Writing|pen|G1|<0.000000, 0.000000, 1.000000>|<0.000000, 0.000000, 0.000000>|right hand

Rez two props when the Sit pose is played:

    PROP Sit|prop1|G1|<0.000000, 0.000000, 1.000000>|<0.000000, 0.000000, 0.000000>
    PROP Sit|prop2|G1|<0.000000, 0.000000, 1.000000>|<0.000000, 0.000000, 0.000000>


### One SITTER

Complete notecard for one SITTER. Includes poses, buttons, different prop types and prop groups:

```
POSE Read|z-readpapers
POSE Dine|table-eat
POSE Soup|table-soup
BUTTON Wine
BUTTON Juice
{Read}<-0.007082, 0.000018, 0.137853><-0.016476, 9.001595, 0.033839>
{Dine}<0.222899, 0.015423, 0.373918><-0.037846, 2.906952, 3.043228>
{Soup}<0.284377, -0.009065, 0.355389><0.257740, 6.912522, 0.014369>
PROP Read|paper|G1|<0.550008, -0.001500, 0.142298>|<-134.045500, 75.901150, 44.793560>
PROP Dine|eggs|G1|<0.469654, 0.000830, 0.191699>|<-0.018939, 9.899974, -0.015683>
PROP1 Dine|knife|G1|<0.387543, -0.311709, 0.173970>|<-0.017549, 9.899983, 90.102720>|Right Hand
PROP1 Dine|fork|G1|<0.386396, 0.315884, 0.173978>|<-0.017549, 9.899983, 90.102720>|Left Hand
PROP Soup|soup|G1|<0.471728, 0.000833, 0.182416>|<-0.017561, 9.899969, 0.005860>
PROP1 Soup|spoon|G1|<0.378329, -0.319233, 0.181404>|<-0.017547, 9.899982, 90.102720>|Right Hand
PROP Wine|wine|G2|<0.778376, -0.371154, 0.302741>|<-0.020984, 9.899971, 0.006449>
PROP Juice|juice|G2|<0.760159, -0.371186, 0.198361>|<-0.020984, 9.899975, 0.006449>
```

### Two SITTERs

Complete notecard for two SITTERs, including props for both SITTERs:

```
SITTER 0
POSE Laptop|z-lt-lie
POSE Sitting|chair-001
SYNC Couples1|fm-close
SYNC Couples2|fm-entwine
{Laptop}<0.042650, -0.772460, 0.296690><0.000000, -11.995530, 0.000000>
{Sitting}<0.224900, -0.734250, 0.744080><0.000000, 0.000000, 0.000000>
{Couples1}<0.180660, 0.019210, 0.433470><1.569690, 18.286940, -8.538540>
{Couples2}<0.586030, 0.351290, 0.145940><0.000000, 0.000000, 175.963300>
PROP Laptop|laptop|G1|<0.433091, -0.835237, 0.319153>|<-122.413500, 71.813410, 31.093090>
PROP Couples1|laptop|G1|<0.319954, -0.866334, 0.312684>|<108.560600, -60.579450, -163.669100>

SITTER 1
POSE Laptop|z-lt-tummy
POSE Sitting|chair-001
SYNC Couples1|ml-close
SYNC Couples2|ml-entwine
{Laptop}<0.239970, 0.651860, 0.258480><-5.942750, -0.826550, -74.043050>
{Sitting}<0.223270, 0.651870, 0.775510><0.000000, 0.000000, 0.000000>
{Couples1}<0.348780, 0.037700, 0.212590><1.569690, 18.286940, -8.538540>
{Couples2}<0.545530, 0.215300, 0.222410><0.000000, 0.000000, 176.003400>
PROP Laptop|laptop|G1|<0.466172, -0.140335, 0.311097>|<98.181810, 13.074120, 178.024700>
PROP Couples1|laptop|G1|<0.319954, 0.837922, 0.312684>|<-105.833200, -55.077900, -13.040110>
```

### AVmenu&trade; Example

Example notecard for [AV]menu with [AV]prop. Demonstrates use of prop groups (shelf1,shelf2,shelf3).

```
TEXT Welcome to my display case :)\nChoose items to rez!\n
BUTTON Books
BUTTON Glasses
BUTTON Photo
BUTTON Fruit
BUTTON Plates
BUTTON Vase
BUTTON [CLEAR]
PROP Books|books|shelf1|<-0.042320, 0.020645, 1.875854>|<0.000000, 0.000000, 0.000000>
PROP Glasses|glasses|shelf1|<-0.270195, -0.014359, 1.763062>|<0.000000, 0.000000, -84.350010>
PROP Photo|photo|shelf2|<-0.001717, -0.056343, 1.234741>|<78.650010, 6.850002, 1.349999>
PROP Fruit|fruit|shelf2|<0.014526, 0.002861, 1.214783>|<180.000000, 0.000000, 0.000000>
PROP Plates|plates|shelf3|<0.199730, -0.000938, 0.434692>|<-90.000000, 73.000010, 0.000000>
PROP Vase|vase|shelf3|<-0.022728, -0.019066, 0.440918>|<0.000000, 0.000009, 174.400100>
```

{% include tip.html content="For working examples, see the [AV]prop examples provided to you in the Plugins Examples [BOX]." %}

## LSL Scripting
Scripting methods can be used to rez and remove props, and respond to prop related events.

{% include warning.html content="Don't use this section without a knowledge of [LSL scripting](http://wiki.secondlife.com/wiki/LSL_Portal)." %}


### LSL Link Messages to Send

#### Message 90200 & 90220

Instructs [AV]prop to rez a prop by its &lt;trigger_name&gt;. e.g.

    llMessageLinked(LINK_THIS, 90220, "Fruit", "");

By including an avatar's &lt;avatar_uuid&gt; you can rez the prop specifically for them. e.g.

    llMessageLinked(LINK_THIS, 90220, "Fruit", <avatar_uuid>);

By including an integer you can rez the prop specifically for that sitter. e.g.

    llMessageLinked(LINK_THIS, 90220, "Fruit", "0");

If you want to clear all props then use a &lt;trigger_name&gt; that does not match a prop. e.g.

    llMessageLinked(LINK_THIS, 90220, "[CLEAR]", "");

To derez a specific prop by name, just add "remprop_" to the beginning of the &lt;trigger_name&gt;. e.g.

    llMessageLinked(LINK_THIS, 90220, "remprop_Fruit", "");

{% include important.html content="If you want the menu returned to the avatar, use 90200 instead of 90220." %}

{% include note.html content="The [AV]prop script can be used by itself to create a rezzing prim where props defined in an AVpos notecard are rezzed entirely via link messages (i.e. without sit scripts in the same prim)." %}

{% include note.html content="Link Messages that rez/derez props must be sent from the same prim the props are in." %}

### LSL Link Messages to Receive

#### Message 90500

[AV]prop reports on events relating to props with link message 90500. The key field will include the UUID of the avatar. The string field includes the event type, SITTER #, &lt;trigger_name&gt;, &lt;prop_object&gt;, &lt;prop_group&gt; & the prop's UUID, each separated by the pipe ( &#124; ) character (to separate this information, llParseStringKeepNulls(); is used). Possible event types are ATTACHED, DETACHED, REZ, DEREZ. This information may be useful to trigger scripted actions in certain advanced projects.

e.g.

```js
default
{
    link_message(integer sender, integer num, string msg, key id)
    {
        if(num == 90500)
        {
            list data = llParseStringKeepNulls(msg, ["|"], []);
            key AVATAR_UUID = id;
            string EVENT = llList2String(data, 0);
            string SITTER_NUMBER = llList2String(data, 1);
            string PROP_NAME = llList2String(data, 2);
            string PROP_OBJECT = llList2String(data, 3);
            string PROP_GROUP = llList2String(data, 4);
            string PROP_UUID = llList2String(data, 5);
            llOwnerSay(llDumpList2String([EVENT, SITTER_NUMBER, PROP_NAME, PROP_OBJECT, PROP_GROUP, PROP_UUID, AVATAR_UUID], ","));
        }
    }
}
```

### Script Examples
For AVprop script examples click [here](/avsitter2_lsl_examples_avprop.html).

{% include links.html %}
