---
title: AVcontrol&trade;
keywords: plugin, control
sidebar: avsitter2_sidebar
permalink: avsitter2_control.html
folder: avsitter2
---

## AVcontrol&trade;

The AVcontrol&trade; plugin adds specialized features to AVsitter&trade; furniture including for photo studio or furniture where one avatar wants to control the menu of another avatar. The plugin also includes scripts for compatibility with some popular 3rd party adult roleplay systems in SL such as [RLV](http://wiki.secondlife.com/wiki/Third_Party_Viewer_Directory/Restrained_Love), [Xcite!](https://www.getxcite.com/) and [Lockguard](http://lslwiki.net/lslwiki/wakka.php?wakka=exchangeLockGuard).

{% include important.html content="AVcontrol scripts and examples are found inside the AVcontrol [BOX] (inside the Plugins [BOX])." %}

### [AV]root-control script
The [AV]root-control script allows menus of sitting avatars to be controlled by another avatar. e.g. for photo studio.

To use this feature, start with the <a href="/avsitter2_home.html#setup">normal setup</a> procedure, then:

- Drop the [[AV]root-security](avsitter2_utilities.html#avroot-security-script) script into the *root prim* of your furniture. (Utilities box)
- Remove the [[AV]root](avsitter2_utilities.html#avroot-script) script, if you were using it.
- Drop the [AV]root-control script into the *root prim* of your furniture.
- Anyone can now touch the furniture to control the menu of the sitting avatars, depending on the security level.

### [AV]root-RLV script
The [AV]root-RLV script allows you to add RLV (Restrained Love Viewer) functions to your furniture. Specifically, it allows an avatar to *capture* other avatars and impose RLV restrictions upon them. To be controlled by RLV, avatars *must* be wearing an *RLV relay* based on the [RLV API](http://wiki.secondlife.com/wiki/LSL_Protocol/RestrainedLoveAPI) (e.g. [OpenCollar](http://opencollar.at)), and turn on RLV in the SL viewer.

To use this feature:

- Start with the instructions for [[AV]root-control](avsitter2_control.html#avroot-control-script).
- Drop the [AV]root-RLV script into the *root prim* of your furniture.
- Place a notecard named AVpos into the *root prim* of your furniture (if there is not one already there).

{% include important.html content="If working with a couples setup and RLV, the sitA+sitB scripts *must* be in the root prim." %}

{% include important.html content="The [AV]root-RLV script can not be used when assigning SitTargets for [multiple SET](avsitter2_sittargets.html) in the same object." %}

{% include tip.html content="For examples, see the [[AV]control examples](avsitter2_control.html#examples) provided to you in the AVcontrol [BOX]." %}

#### Capture behavior

{% include note.html content="Selecting an avatar for capture will force them to sit on the furniture and the menu will be 'locked', meaning that only the controlling avatar can access the menu. The timelock countdown *is not* automatically started." %}

{% include note.html content="If an avatar sits voluntarily and is captured then the menu will be 'unlocked', meaning that any non-captured avatar can take control of the menu. The timelock countdown is automatically started." %}

{% include note.html content="When an avatar is released, any RLV restrictions imposed by the furniture are removed." %}

#### Control menu

The Control menu contains the following options:

- **Capture!** - capture the avatar.
- **Release!** - release the captive avatar.
- **Take Keys/Drop Keys** - allows the controlling avatar to "lock" or "unlock" the menu.  
- **Timelock** - start/stop/change the countdown timer for automatic release.
- **Restrict** - available only if the [AV]root-RLV-extra script is included (see below).
- **Un/Dress** - available only if the [AV]root-RLV-extra script is included (see below).
- **Menu** - goes to the regular pose menu of the captive avatar.
- **[STOP]** - releases and unsits all avatars.

{% include important.html content="For testing, you can enable RLV debug messages in your SL viewer's menu under **'RLV>Debug>Show Debug Messages'**." %}

#### AVpos Notecard

The AVpos notecard can include the following RLV related settings, placed at the top of the notecard.

**RLV** - if the RLV capture and menu restrictions should be enabled (default is 1). Switch off to adjust poses. e.g.

	RLV 0

**ROLES** - the roles (either 'D' for 'Dominant' or 'S' for 'Submissive') for each avatar, separated by the pipe (`|`) character. e.g. 

	ROLES D|S

The number of entries must correspond exactly to the number of SITTER lines in the AVpos notecard. For multiple solo-sitter setups in child prims the entries must correspond to the number of separate solo-sitter prims and must all be defined as 'S'.

{% include note.html content="When there are no more 'S' seats available, the script will not offer the capture option." %}

{% include note.html content="Avatars in 'S' seats can not access the menu unless you use the SUBCONTROL option (see below)." %}

**ONTOUCH** - what happens when furniture with no sitting avatars is touched. Options are:

- **ASK** - search for RLV relays in range (20m) and ask who to capture. (default)
- **CAPTURE** - attempt to capture the avatar who touched it (if they are wearing an RLV relay).
- **NONE** - do nothing if touched when there are no sitting avatars.

e.g.

	ONTOUCH CAPTURE

**ONSIT** - what happens when someone sits voluntarily. Options are:

- **ASK** - ask the avatar to choose between 'D' and 'S' roles. On choosing, the avatar will be moved to the first available sitter defined for that role by the ROLES setting, or unseated if no seats for that role are available. Choosing 'S' role will attempt to capture the avatar.
- **ASKONLY** - same as ASK, but choosing the 'S' role will not attempt to capture. They can still be captured via the menu.
- **CAPTURE** - sitting will attempt to capture the avatar (if they are wearing an RLV relay). (default)
- **NONE** - sitting voluntarily on the furniture will not attempt to capture the avatar.

e.g.

	ONSIT ASK

{% include note.html content="When using ONSIT ASK or ONSIT ASKONLY, the regular [SWAP] button is removed from the menu." %}

**ONCAPTURE** - a list of [RLV commands](http://wiki.secondlife.com/wiki/LSL_Protocol/RestrainedLoveAPI) to issue when an avatar is captured, each separated by the pipe (`|`) character (default is `@unsit=n`). e.g.

	ONCAPTURE @unsit=n|@fartouch=n|@rez=n|@edit=n|@acceptpermission=add

**ONRELEASE** - a list of [RLV commands](http://wiki.secondlife.com/wiki/LSL_Protocol/RestrainedLoveAPI) to issue when an avatar is released, each separated by the pipe (`|`) character (default is `@unsit=force`). If you don't want to unsit avatars when they are released then define ONRELEASE <ins>not</ins> to use `@unsit=force`. e.g.

	ONRELEASE @unsit=y

**WAITPOSE** - optional POSE to play while waiting for the avatar to choose their role. Only applicable when using ONSIT ASK. e.g.

	WAITPOSE standby

When used, a pose of the specified name (e.g. 'POSE standby') should be present in all sitter menus. If you don't want the WAITPOSE showing in the menu then you can place it in a MENU that has no corresponding TOMENU in the AVpos notecard, as described [here](avsitter2_sequence.html#hiding-poses).

**DOMPOSE** - optional POSE to play when an avatar chooses the 'D' role. Only applicable when using ONSIT ASK. e.g.

	DOMPOSE Dom1

**SUBPOSE** - optional POSE to play when an avatar chooses the 'S' role. Only applicable when using ONSIT ASK. e.g.

	SUBPOSE cross

**RECAPTURE** - if captives should be automatically re-captured if they log out before being released (default is 0). e.g.

	RECAPTURE 1

{% include important.html content="Note that for recapture to work, it must be supported by the RLV Relay being used (see [here](http://avsitter.com/qa/955))." %}

**TIMELOCK** - the initial setting for the timelock in minutes (default is 0). e.g.

	TIMELOCK 5

**SUBCONTROL** - if submissives should be allowed to access their own pose menu (default is 0). e.g.

	SUBCONTROL 1

You can also put `@touchworld=n` in your ONCAPTURE list to prevent submissives touching the furniture for menu when captured. 

**HTEXT** - if hovertext should be set on the root prim showing the RLV status (default is 1). Offset height by using a number >1. e.g.

	HTEXT 0 or HTEXT 10

If you want to show the hovertext on a different prim then use HTEXT 0 and link message 90207 in your own script. e.g:

```js
default
{
    link_message(integer sender, integer num, string text, key suggested_color)
    {
        if(num == 90207)
        {
            llSetText(text, (vector)((string)suggested_color), 1);
        }
    }
}
```

#### Example settings

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

{% include tip.html content="For more examples, see the [[AV]control examples](avsitter2_control.html#examples) provided to you in the AVcontrol [BOX]." %}

### [AV]root-RLV-extra script

Adding this optional script will provide additional RLV Restrict and Un/Dress menus, which include the following options:

- **Restrict** - toggle various RLV restrictions on the captive.
- **Browse #RLV** - browse the avatar's #RLV folder and wear/unwear folders they have set up.  
- **Fast Strip** - remove every item of clothing and attachments from all attachment points (except skull).
- **Undress** - remove individual clothing layers.
- **Detach** - remove attachments from individual attachment points.

{% include important.html content="Folders starting with a period ( . ) can not be browsed, and adding *(nostrip)* to an item's name or folder will prevent it from being removed. Many guides such as [OpenCollar's smartstrip guide](https://raw.githubusercontent.com/OpenCollar/opencollar/master/src/spares/readme_smartstrip) discuss #RLV folder setup." %}

### LSL Scripting

A link message exists so scripters can make things happen when avatars are captured/released. See [here](http://avsitter.com/qa/501).

### [AV]Xcite! script
This optional script allows you to make your AVsitter&trade; furniture compatible with Xcite! and Sensations products in SL.

{% include note.html content="Instructions for the [AV]Xcite! script are included within the [AV]Xcite_settings notecard." %}

{% include important.html content="You must include a copy of your Xcite! partner script (provided by Xcite!) and/or your Sensations partner script (provided by Sensations) in your furniture." %}

{% include note.html content="Xcite! compatible features should be switched on/off via the product's menu (e.g. on the HUD provided with the Xcite! or Sensations product menu)." %}

### [AV]LockGuard script
This optional script allows you to make your AVsitter&trade; furniture work with [LockGuard V2](http://wiki.secondlife.com/wiki/LSL_Protocol/LockGuard) compatible cuffs (e.g. [OpenCollar](http://opencollar.at)) for particle chains. Details for use are included within the [AV]LockGuard script itself.

## Examples
The following Examples are provided in the AVcontrol box:

- **Photo Stand**
Basic example of the [AV]root-control script for a non-RLV situation.  
- **Photo Stand, multiple setup prims**
Example of the [AV]root-control script for a non-RLV situation, with multiple setup prims.
- **RLV & LockGuard, 1 sub**
RLV for 1 submissive.
- **RLV & LockGuard, Dom+sub**
RLV for 1 submissive and 1 dominant (ONSIT ASK).
- **RLV & LockGuard, 2 subs**
RLV for 2 submissives (with [SitTargets defined](avsitter2_sittargets.html) so avatars will be captured on to the prim that was last touched).
- **RLV & LockGuard, Dom+2 subs**
RLV for 2 submissives and 1 dominant (ONSIT ASK).
- **RLV & LockGuard, multiple setup prims**
RLV for 2 submissives, set in multiple setup prims.
- **RLV & Props, Dom+sub**
RLV for 1 submissive and 1 dominant (With multiple <a href="/avsitter2_prop.html">prop</a> examples).
- **RLV Cage Example, 1 sub**
Cage example for 1 submissive (SUBCONTROL 1).
- **LockGuard attaching to Props, 1 sub**
Attaching particle chains to props.
- **RLV Sofa Example, Dom+sub**
Example of use in "normal" furniture (SUBCONTROL 1, ONTOUCH NONE, ONSIT NONE).
- **RLV bed Example, Dom+2 subs**
Example of use in "normal" furniture (SUBCONTROL 1, ONTOUCH NONE, ONSIT ASKONLY).

{% include important.html content="OpenCollar cuffs provided in [examples](avsitter2_examples.html) are for demonstration only. Current versions should be obtained from [OpenCollar](http://opencollar.at)." %}


{% include links.html %}
