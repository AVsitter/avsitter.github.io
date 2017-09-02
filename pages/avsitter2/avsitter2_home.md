---
title: AVsitter2
summary:
keywords: AVsitter2
sidebar: avsitter2_sidebar
toc: true
permalink: avsitter2_home.html
folder: avsitter2
---

## How to get AVsitter2

AVsitter2 can be freely obtained from GitHub and imported into Second Life by following our <a href='https://github.com/AVsitter/AVsitter/blob/master/AVsitter2/IMPORT_GUIDE.md'>import guide</a>.

{% include tip.html content="If you would prefer a packaged version of the latest release, and to receive packaged in-world updates of future releases, visit the <a href='https://marketplace.secondlife.com/stores/79645'>SL Marketplace</a>. Proceeds from marketplace sales are shared with open-source contributors and help support continued development." %}

## Inside the AVsitter2 Package

The main AVsitter package contains:

-  <b>[AV]sitA & [AV]sitB scripts</b>

   The main scripts that must always be used in a pair (A+B), one pair for each avatar to sit. Each pair will define a SITTER.

-  <b>[AV]adjuster script & [AV]helper object</b>

   These are setup items that allow the default pose positions to be adjusted.

-  <b>AVpos notecard</b>

   AVsitter data needs to be saved in an AVpos notecard. The notecard provided is intentionally empty.

-  <b>Examples [BOX]</b>

   The AVsitter Examples [BOX] contains <a href="/avsitter2_examples.html">several example items</a> that demonstrate the use of the system. The imprtance of the examples is often overlooked. Please examine the examples closely to understand how the system can be used for different setups.

-  <b>Utilities [BOX]</b>

   The Utilities [BOX] contains the <a href="/avsitter2_utilities.html">Utilities</a>.

-  <b>Plugins [BOX]</b>

   The Plugins [BOX] contains scripts that provide special functionality, along with <a href="/avsitter2_examples.html">examples</a>. Example items are provided for each script.

## Requirements

There are some basic requirements to use AVsitter:

<ul>
<li/>You will need to have a beginner's <a href="http://wiki.secondlife.com/wiki/Building_Tools">knowledge of building in Second Life</a>.
<li/>You will need to purchase animation files from <a href="http://bit.ly/HtdEqK">animation stores in SL</a> or <a href="http://wiki.secondlife.com/wiki/How_to_create_animations">learn to create them yourself</a>.</ul>

## Setup

### Basic Prim Setup

The most basic setup is a prim that seats one avatar.

<ol>
<li/>Drop the following into an empty prim in your furniture:

<ul>
<li/>[AV]sitA + [AV]sitB scripts
<li/>[AV]adjuster script
<li/>[AV]helper object
<li/>AVpos notecard
<li/>The animation files you plan to use
</ul>
{% include note.html content="One pair of [AV]sit (A+B) scripts will mean the prim has <i>one</i> SITTER." %}

<li/>Sit on your furniture, and the menu will appear (if you lose the menu just touch your furniture again to get the menu back).

<li/>Choose [ADJUST] then [HELPER] from the menu, and the [AV]helper stick will rez.

<li/>Choose [NEW] from the menu, then choose [POSE] to create a singles pose.

<li/>After creating a pose, adjust its position by moving the helper stick with the SL building tools until your avatar is in the correct position. Click [SAVE] for each pose you create before moving on to the next.

<li/>When you have finished saving all your poses, click [DUMP] to output your settings into chat.

{% include note.html content="If you use a translator, turn it off before pressing [DUMP]." %}

<li/>Copy-paste the [DUMP] result into your AVpos notecard, replacing the contents of the notecard.

{% include note.html content="A web link is now given as a link at the end of the settings [DUMP], which is more reliable than copying from SL chat." %}

<li/>If required, you can rez the [HELPER] again and add more poses.

<li/>To add poses to other prims in your object, simply repeat the process.
</ol>
<br>
{% include important.html content="When you [DUMP] you'll see the diamond character (&diams;) on every line. All text on a notecard line before the diamond is ignored by the script. This allows you to copy-paste chat output directly into your notecard without having to remove the timestamp from every line. If you remove the timestamps from your notecard then you can safely remove the diamonds." %}

{% include tip.html content="Once setup is complete, you can (optionally) remove the [AV]helper and [AV]adjuster from your furniture. Leaving them in will allow the <u>next owner</u> to modify and [SAVE] the default pose positions (although they will not have access to [DUMP] or [NEW] unless they are an AVsitter2 owner)." %}

<br>
<b>Basic Setup Video</b>

<iframe height="349" src="https://www.youtube.com/embed/Oie421iU1P8?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>

{% include tip.html content="If English is not your language, the videos have captions for automatic translation." %}

### Couples Prim Setup

Setup of a prim for multiple avatars is the same as for <a href="/avsitter2_home.html#basic-prim-setup">Basic Prim Setup</a>, with a few additions:

<ol>
<li/>Your object must have a prim count equal to or greater than the number of avatars you plan on sitting.

<li/>You will need to drop one pair of [AV]sit (A+B) scripts into the prim <i>for each avatar you want to sit</i>.
i.e. For 2 sitters you'll need 2 pairs of [AV]sit (A+B) scripts.

{% include note.html content="SL should automatically name your scripts sequentially when you drop them in together. Please make sure it does this correctly, as the names must be sequential. i.e. [AV]sitA, [AV]sitA 1, [AV]sitB, [AV]sitB 1" %}

<li/>In the [NEW] menu, choosing [POSE] will create a singles pose and choosing [SYNC] will create a couples pose.

{% include note.html content="Choosing [POSE] will add a singles POSE only to the menu of the SITTER <i>you are on</i>. Press [SWAP] first if you need to move to a different SITTER's menu before adding the pose. The active SITTER # is listed in the menu." %}

{% include note.html content="Choosing [SYNC] will add a SYNC pose to the menu of <i>multiple SITTERs</i> (e.g. SITTER 0 and SITTER 1)." %}

{% include important.html content="Singles poses should be positioned so that they do not overlap the positions set for other sitters. e.g. SITTER 0 poses on left-hand side of the furniture, and SITTER 1 on right-hand side." %}

{% include important.html content="The first pose in each SITTER is the default pose for the seat. Even in couples furniture, you should usually make the first pose in each SITTER's menu a singles POSE." %}

</ol>
<br>
<b>Couples Setup Video</b>

<iframe height="349" src="https://www.youtube.com/embed/A0O83Y8zqUw?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>

{% include tip.html content="If English is not your language, the videos have captions for automatic translation." %}

### Submenus

To create a submenu...

<ol>
<li/>In the [NEW] menu, choose [SUBMENU]. This will create a submenu <u>only in the menu of the SITTER you are on</u>.
<li/>Navigate to your submenu and then create new [POSE], [SYNC], or [SUBMENU] inside the submenu.
</ol>

{% include note.html content="[SUBMENU] will only add to the menu of the SITTER you are on. If want to have the same submenu in another SITTER's menu, you will need to press [SWAP] to move to the other SITTER and create the submenu there too." %}

{% include important.html content="If adding a [SYNC] pose, the pose will be added to whichever submenu was last selected. This applies separately to each SITTER's menu. You will need to press [SWAP] to move to the other SITTER and create/select the submenu there too." %}

{% include important.html content="Adding poses to submenus via the [NEW] menu is for beginners. You can create, re-order, rename, delete submenus by learning the TOMENU and MENU commands covered in the <a href='/avsitter2_avpos.html'>Notecard Section</a>." %}

### Camera

To save a camera position... 

<ol>
<li/>In the [NEW] menu, choose [CAMERA] then [SAVE]. This will save your camera view for all sitters in the prim.
<li/>To remove all camera settings from the object, choose [CAMERA] then [CLEAR].
<li/>Changes to camera settings will take effect the next time you sit.
</ol>

{% include note.html content="The camera setting is a prim property and does not require anything to be placed in the AVpos notecard." %}

{% include warning.html content="For camera settings in multiple prims, be aware of JIRA <a href=\"https://jira.secondlife.com/browse/BUG-5494\">BUG-5494</a>." %}

{% include note.html content="If you need a different camera position for each pose, see information for the <a href='/avsitter2_camera.html'>[AV]camera script</a> instead." %}

### Chat Commands

The following chat commands can be typed into local chat while the [AV]adjuster and [AV]helper are in the furniture:

<ul>
<li/>/5 helper - rezzes the helpers (alternate to using menu).

<li/>/5 cleanup - deletes the [AV]adjuster & [AV]helper from the prim.

<li/>/5 &lt;avatar uuid&gt; - moves the helper into the exact position of another avatar. Useful for copying positions from poseballs. 

<li/>/5 targets - briefly shows the <a href="/avsitter2_sittargets.html">SitTargets</a> in hovertext.</ul>

### Making Corrections

If you do not get things right the first time, you can always make corrections or additions:

<ul>
<li/>To change the position of a pose, or to add new poses, you can always select [HELPER] again, position the pose, and [SAVE]. Remember to [DUMP] your settings again and save them to the AVpos notecard after making any changes.

<li/>If you want to rename or change the order of any menu items you can manually edit <a href="/avsitter2_avpos.html">the AVpos notecard</a>.

<li/>To delete a pose, you must manually remove the lines from the <a href="/avsitter2_avpos.html">the AVpos notecard</a>.

<li/>As with all building in SL, you should take a backup of your work regularly to avoid losing progress.  

</ul>

## Advanced Setup

The [NEW] menu described on this page is a great way to start using AVsitter, however you will have much more control when you learn to edit the notecard manually. After you can follow the tutorials on this page you should then learn the format of the <a href="/avsitter2_avpos.html">AVpos notecard</a> and learn about the <a href="/avsitter2_utilities.html">utility scripts</a>. Advanced users can then consider <a href="/avsitter2_scripting.html">custom scripting</a> or one of the available plugins.

### Multiple Setups

It is possible to have any mix of singles & couples setups in different prims of the same furniture, however you must follow the instructions given in the <a href="/avsitter2_sittargets.html">SitTargets section</a>.

### Setups for 3+ Avatars

Setups in one prim for 3+ avatars is the same as for <a href="/avsitter2_home.html#couples-prim-setup">couples setup</a> but needs to include more pairs of [AV]sit (A+B) scripts. The [NEW] menu will allow you to add a SYNC pose for multiple SITTERs but you should also learn to add/edit poses <a href="/avsitter2_avpos.html">manually in the notecard</a>.

{% include note.html content="If your furniture does not include SYNC poses you could instead set each avatar's poses in separate prims. e.g. a table with 4 chairs around would usually be best with a singles setup in each chair, rather than 4 SITTERs in one." %}

{% include warning.html content="There is no set limit but it's not recommended to have more than 6 SITTERs in the same prim." %}

### Animation Sequences

AVsitter provides two ways to do sequences: the <a href="/avsitter2_sequence.html">AVsequence&trade;</a> script and the <a href="/avsitter2_avpos.html#built-in-animation-sequence">"built-in" sequence</a> method. Read about both and use the method most appropriate for your situation.

### Sounds and Songs

Playing sound files is achieved with the <a href="/avsitter2_sequence.html">AVsequence&trade;</a> script (includes playing a single sound with a pose, or a complete song).

{% include links.html %}
