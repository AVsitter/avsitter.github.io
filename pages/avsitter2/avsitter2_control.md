---
title: AVcontrol&trade;
keywords: plugin, control
sidebar: avsitter2_sidebar
permalink: avsitter2_control.html
folder: avsitter2
---

## AVcontrol&trade;

The AVcontrol&trade; plugin adds specialized features to AVsitter&trade; furniture including for photo studio or furniture where one avatar wants to control the menu of another avatar. The plugin also includes scripts for compatibility with some popular 3rd party adult roleplay systems in SL such as <a href="http://wiki.secondlife.com/wiki/Third_Party_Viewer_Directory/Restrained_Love">RLV</a>, <a href="https://www.getxcite.com/">Xcite!</a> and <a href="http://lslwiki.net/lslwiki/wakka.php?wakka=exchangeLockGuard">Lockguard</a>.

{% include important.html content="AVcontrol scripts and examples are found inside the AVcontrol [BOX] (inside the Plugins [BOX])." %}

### [AV]root-control script
The [AV]root-control script allows menus of sitting avatars to be controlled by another avatar. e.g. for photo studio.

To use this feature, start with the <a href="/avsitter2_home.html#setup">normal setup</a> procedure, then:

<ol>
<li/>Drop the <a href="/avsitter2_utilities.html#avroot-security-script">[AV]root-security</a> script into the <i>root prim</i> of your furniture. (Utilities box)

<li/>Remove the <a href="/avsitter2_utilities.html#avroot-script">[AV]root</a> script, if you were using it.

<li/>Drop the [AV]root-control script into the <i>root prim</i> of your furniture.

<li/>Anyone can now touch the furniture to control the menu of the sitting avatars, depending on the security level.
</ol>

### [AV]root-RLV script
The [AV]root-RLV script allows you to add RLV (Restrained Love Viewer) functions to your furniture. Specifically, it allows an avatar to <i>capture</i> other avatars and impose RLV restrictions upon them. To be controlled by RLV, avatars <i>must</i> be wearing an <i>RLV relay</i> based on the <a href=http://wiki.secondlife.com/wiki/LSL_Protocol/RestrainedLoveAPI>RLV API</a> (e.g. <a href="http://opencollar.at">OpenCollar</a>), and turn on RLV in the SL viewer.

To use this feature:

<ol>
<li/>Start with the instructions for <a href="/avsitter2_control.html#avroot-control-script">[AV]root-control</a>.

<li/>Drop the [AV]root-RLV script into the <i>root prim</i> of your furniture.

<li/>Place a notecard named AVpos into the <i>root prim</i> of your furniture (if there is not one already there).
</ol>

{% include important.html content="If working with a couples setup and RLV, the sitA+sitB scripts <i>must</i> be in the root prim." %}

{% include important.html content="The [AV]root-RLV script can not be used when assigning SitTargets for <a href='/avsitter2_sittargets.html'>multiple SET</a> in the same object." %}

{% include tip.html content="For examples, see the <a href='/avsitter2_control.html#examples'>[AV]control examples</a> provided to you in the AVcontrol [BOX]." %}

<br>
<b>Capture behavior</b>

{% include note.html content="Selecting an avatar for capture will force them to sit on the furniture and the menu will be 'locked', meaning that only the controlling avatar can access the menu. The timelock countdown <i>is not</i> automatically started." %}

{% include note.html content="If an avatar sits voluntarily and is captured then the menu will be 'unlocked', meaning that any non-captured avatar can take control of the menu. The timelock countdown is automatically started." %}

{% include note.html content="When an avatar is released, any RLV restrictions imposed by the furniture are removed." %}

<br>
<b>Control menu</b>

The Control menu contains the following options:

<ol>
<li/><b>Capture!</b> - capture the avatar.
<li/><b>Release!</b> - release the captive avatar.
<li/><b>Take Keys/Drop Keys</b> - allows the controlling avatar to "lock" or "unlock" the menu.  
<li/><b>Timelock</b> - start/stop/change the countdown timer for automatic release.
<li/><b>Restrict</b> - available only if the [AV]root-RLV-extra script is included (see below).
<li/><b>Un/Dress</b> - available only if the [AV]root-RLV-extra script is included (see below).
<li/><b>Menu</b> - goes to the regular pose menu of the captive avatar.
<li/><b>[STOP]</b> - releases and unsits all avatars.
</ol>

{% include important.html content="For testing, you can enable RLV debug messages in your SL viewer's menu under <b>'RLV>Debug>Show Debug Messages'</b>." %}

<br>
<b>AVpos Notecard</b>

The AVpos notecard can include the following RLV related settings, placed at the top of the notecard.

<b>RLV</b> - if the RLV capture and menu restrictions should be enabled (default is 1). Switch off to adjust poses. e.g.

	RLV 0

<b>ROLES</b> - the roles (either 'D' for 'Dominant' or 'S' for 'Submissive') for each avatar, separated by the pipe ( &#124; ) character. e.g. 

	ROLES D|S

The number of entries must correspond exactly to the number of SITTER lines in the AVpos notecard. For multiple solo-sitter setups in child prims the entries must correspond to the number of separate solo-sitter prims and must all be defined as 'S'.

{% include note.html content="When there are no more 'S' seats available, the script will not offer the capture option." %}

{% include note.html content="Avatars in 'S' seats can not access the menu unless you use the SUBCONTROL option (see below)." %}

<br>
<b>ONTOUCH</b> - what happens when furniture with no sitting avatars is touched. Options are:

<ul>
<li/><b>ASK</b> - search for RLV relays in range (20m) and ask who to capture. (default)
<li/><b>CAPTURE</b> - attempt to capture the avatar who touched it (if they are wearing an RLV relay).
<li/><b>NONE</b> - do nothing if touched when there are no sitting avatars.
</ul>
e.g.

	ONTOUCH CAPTURE

<b>ONSIT</b> - what happens when someone sits voluntarily. Options are:

<ul>
<li/><b>ASK</b> - ask the avatar to choose between 'D' and 'S' roles. On choosing, the avatar will be moved to the first available sitter defined for that role by the ROLES setting, or unseated if no seats for that role are available. Choosing 'S' role will attempt to capture the avatar.
<li/><b>ASKONLY</b> - same as ASK, but choosing the 'S' role will not attempt to capture. They can still be captured via the menu.
<li/><b>CAPTURE</b> - sitting will attempt to capture the avatar (if they are wearing an RLV relay). (default)
<li/><b>NONE</b> - sitting voluntarily on the furniture will not attempt to capture the avatar.
</ul>
e.g.

	ONSIT ASK

{% include note.html content="When using ONSIT ASK or ONSIT ASKONLY, the regular [SWAP] button is removed from the menu." %}

<br>
<b>ONCAPTURE</b> - a list of <a href='http://wiki.secondlife.com/wiki/LSL_Protocol/RestrainedLoveAPI'>RLV commands</a> to issue when an avatar is captured, each separated by the pipe ( &#124; ) character (default is @unsit=n). e.g.

	ONCAPTURE @unsit=n|@fartouch=n|@rez=n|@edit=n|@acceptpermission=add

<b>ONRELEASE</b> - a list of <a href='http://wiki.secondlife.com/wiki/LSL_Protocol/RestrainedLoveAPI'>RLV commands</a> to issue when an avatar is released, each separated by the pipe ( &#124; ) character (default is @unsit=force). If you don't want to unsit avatars when they are released then define ONRELEASE <U>not</u> to use @unsit=force. e.g.

	ONRELEASE @unsit=y

<b>WAITPOSE</b> - optional POSE to play while waiting for the avatar to choose their role. Only applicable when using ONSIT ASK. e.g.

	WAITPOSE standby

When used, a pose of the specified name (e.g. 'POSE standby') should be present in all sitter menus. If you don't want the WAITPOSE showing in the menu then you can place it in a MENU that has no corresponding TOMENU in the AVpos notecard, as described <a href="/avsitter2_sequence.html#hiding-poses">here</a>.

<b>DOMPOSE</b> - optional POSE to play when an avatar chooses the 'D' role. Only applicable when using ONSIT ASK. e.g.

	DOMPOSE Dom1

<b>SUBPOSE</b> - optional POSE to play when an avatar chooses the 'S' role. Only applicable when using ONSIT ASK. e.g.

	SUBPOSE cross

<b>RECAPTURE</b> - if captives should be automatically re-captured if they log out before being released (default is 0). e.g.

	RECAPTURE 1

{% include important.html content="Note that for recapture to work, it must be supported by the RLV Relay being used (see <a href='//avsitter.com/qa/955'>here</a>)." %}

<br>
<b>TIMELOCK</b> - the initial setting for the timelock in minutes (default is 0). e.g.

	TIMELOCK 5

<b>SUBCONTROL</b> - if submissives should be allowed to access their own pose menu (default is 0). e.g.

	SUBCONTROL 1

You can also put @touchworld=n in your ONCAPTURE list to prevent submissives touching the furniture for menu when captured. 

<b>HTEXT</b> - if hovertext should be set on the root prim showing the RLV status (default is 1). Offset height by using a number >1. e.g.

	HTEXT 0 or HTEXT 10

If you want to show the hovertext on a different prim then use HTEXT 0 and link message 90207 in your own script. e.g:

```js
default{
    link_message(integer sender, integer num, string text, key suggested_color){
        if(num==90207){
            llSetText(text,(vector)((string)suggested_color),1);
        }
    }
}
```

<b>Example settings<b>

Example for 1 submissive sitter: 

```
RLV 1
ROLES S
ONSIT CAPTURE
ONTOUCH ASK
TIMELOCK 5
RECAPTURE 1
ONCAPTURE @unsit=n|@fartouch=n
```
Example for 1 submissive and 1 Dominant:

```
RLV 1
ROLES S|D
WAITPOSE standby
DOMPOSE Dom1
SUBPOSE cross
ONSIT ASK
ONTOUCH NONE
TIMELOCK 5
ONCAPTURE @unsit=n|@fartouch=n
```
{% include important.html content="RLV settings are not printed out during settings [DUMP]! Remember to leave your settings at the top of the notecard." %}

{% include tip.html content="For more examples, see the <a href='/avsitter2_control.html#examples'>[AV]control examples</a> provided to you in the AVcontrol [BOX]." %}

<br>
<b>[AV]root-RLV-extra script</b>

Adding this optional script will provide additional RLV Restrict and Un/Dress menus, which include the following options:

<ol>
<li/><b>Restrict</b> - toggle various RLV restrictions on the captive.
<li/><b>Browse #RLV</b> - browse the avatar's #RLV folder and wear/unwear folders they have set up.  
<li/><b>Fast Strip</b> - remove every item of clothing and attachments from all attachment points (except skull).
<li/><b>Undress</b> - remove individual clothing layers.
<li/><b>Detach</b> - remove attachments from individual attachment points.
</ol>

{% include important.html content="Folders starting with a period ( . ) can not be browsed, and adding <i>(nostrip)</i> to an item's name or folder will prevent it from being removed. Many guides such as <a href='https://raw.githubusercontent.com/OpenCollar/opencollar/master/src/spares/readme_smartstrip'>OpenCollar's smartstrip guide</a> discuss #RLV folder setup." %}

<br>
<b>LSL Scripting</b>

A link message exists so scripters can make things happen when avatars are captured/released. See <a href="//avsitter.com/qa/501">here</a>.

### [AV]Xcite! script
This optional script allows you to make your AVsitter&trade; furniture compatible with Xcite! and Sensations products in SL.

{% include note.html content="Instructions for the [AV]Xcite! script are included within the [AV]Xcite_settings notecard." %}

{% include important.html content="You must include a copy of your Xcite! partner script (provided by Xcite!) and/or your Sensations partner script (provided by Sensations) in your furniture." %}

{% include note.html content="Xcite! compatible features should be switched on/off via the product's menu (e.g. on the HUD provided with the Xcite! or Sensations product menu)." %}

### [AV]LockGuard script
This optional script allows you to make your AVsitter&trade; furniture work with <a href="http://wiki.secondlife.com/wiki/LSL_Protocol/LockGuard">LockGuard V2</a> compatible cuffs (e.g. <a href="http://opencollar.at">OpenCollar</a>) for particle chains. Details for use are included within the [AV]LockGuard script itself.

## Examples
The following Examples are provided in the AVcontrol box:

<ol>
<li/><b>Photo Stand</b>
<br>Basic example of the [AV]root-control script for a non-RLV situation.  

<li/><b>Photo Stand, multiple setup prims</b>
<br>Example of the [AV]root-control script for a non-RLV situation, with multiple setup prims.

<li/><b>RLV & LockGuard, 1 sub</b>
<br>RLV for 1 submissive.

<li/><b>RLV & LockGuard, Dom+sub</b>
<br>RLV for 1 submissive and 1 dominant (ONSIT ASK).

<li/><b>RLV & LockGuard, 2 subs</b>
<br>RLV for 2 submissives (with <a href="/avsitter2_sittargets.html">SitTargets defined</a> so avatars will be captured on to the prim that was last touched).

<li/><b>RLV & LockGuard, Dom+2 subs</b>
<br>RLV for 2 submissives and 1 dominant (ONSIT ASK).

<li/><b>RLV & LockGuard, multiple setup prims</b>
<br>RLV for 2 submissives, set in multiple setup prims.

<li/><b>RLV & Props, Dom+sub</b>
<br>RLV for 1 submissive and 1 dominant (With multiple <a href="/avsitter2_prop.html">prop</a> examples).

<li/><b>RLV Cage Example, 1 sub</b>
<br>Cage example for 1 submissive (SUBCONTROL 1).

<li/><b>LockGuard attaching to Props, 1 sub</b>
<br>Attaching particle chains to props.

<li/><b>RLV Sofa Example, Dom+sub</b>
<br>Example of use in "normal" furniture (SUBCONTROL 1, ONTOUCH NONE, ONSIT NONE).

<li/><b>RLV bed Example, Dom+2 subs</b>
<br>Example of use in "normal" furniture (SUBCONTROL 1, ONTOUCH NONE, ONSIT ASKONLY).

</ol>

{% include important.html content="OpenCollar cuffs provided in <a href='/avsitter2_examples.html'>examples</a> are for demonstration only. Current versions should be obtained from <a href='http://opencollar.at'>OpenCollar</a>." %}


{% include links.html %}
