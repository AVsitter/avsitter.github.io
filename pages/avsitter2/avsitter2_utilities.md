---
title: Utilities
keywords: AVsitter2
sidebar: avsitter2_sidebar
permalink: avsitter2_utilities.html
folder: avsitter2
---

## Utilities

The following *optional* scripts are found in the AVsitter [BOX] or Utilities [BOX]:

### [AV]root script
If your object does *not* include a SITTER *inside the root prim* then you can drop this script into the root prim. This will allow sitting avatars to touch anywhere on the furniture to get the menu, instead of having to touch the prim containing the AVsit scripts.

{% include note.html content="The root prim is the main prim of an object. When you select an object, the root prim is highlighted in yellow. The root prim is always defined as the last prim you selected before linking prims together in SL." %}

{% include important.html content="If touching the root prim controls something else in your project, you might not want to include this script." %}

### [AV]root-security script
If you wish to include a security function, place this script in the root prim of your object. The security level can then be changed by the owner in the [ADJUST] menu, with separate options for both "Sit" and "Menu" access. Options are ALL, OWNER or GROUP.

{% include important.html content="If you were using the [AV]root script, delete it and replace it with the [AV]root-security script." %}

{% include note.html content="In GROUP ONLY mode, the avatar must have set their active group to the same group the furniture is set to." %}

### [AV]select script
If you have a setup with more than one SITTER then you may prefer to offer a menu of the different seats instead of having the usual [SWAP] ability which just moves an avatar to the next seat.

- Simply place the [AV]select script in the prim that contains your SITTERs. [SWAP] is now removed and a [BACK] button is added to the top level of the pose menu. When an avatar chooses this [BACK] button they are taken to a menu of the sitters defined in the notecard.
- When the SITTER has only one pose, then the pose name will be used as the button for the sitting location. When the SITTER has multiple poses the [AV]select menu name for a sitting location will be "Sitter 0", "Sitter 1", etc. To set your own name for a sitting location, add it to the end of the SITTER line in the AVpos notecard [as described in the Notecard Commands section](/avsitter2_avpos.html#sitter):

    SITTER 0|Female

- If a singles POSE is playing, [AV]select will show a disabled symbol (<span style="font-size:150%;">&oslash;</span>) in the menu if a seat is occupied by another avatar. When a couples SYNC pose is playing, [AV]select will allow swapping with an occupied seat. You can switch off the disabled symbol to always allow swapping by including [SELECT 1](/avsitter2_avpos.html#select) in your AVpos notecard.

{% include important.html content="The [AV]select script is *NOT* compatible with the [AV]root-control script from the AVcontrol&trade; plugin!" %}

{% include tip.html content="For working examples, see the [AV]select examples provided to you in the Examples [BOX]." %}

### AVhipfix animation
Some animations in SL are not properly designed for furniture, made especially clear when there is no "Hip-Joint" rotation in the animation. In this case the animation will adopt the hip rotation of whichever animation was played last, causing unreliable rotation. If you are experiencing this problem with an animation, you can drop the AVhipfix animation into your setup. AVsitter will automatically recognize this animation and apply a neutral rotation to the "Hip-Joint".

After adding AVhipfix you should re-adjust and [SAVE] the positions of all affected poses so that they are positioned correctly. This is because the original saved position may have been based on the broken "Hip-Joint". If this fixes the issue then we know it was due to a missing "Hip-Joint" rotation in the animation file.

{% include warning.html content="Not all animations are designed for furniture, as the whole body isn't animated (like drinking or waving animations). Animations missing rotations in other joints will cause unpredictability, and they should not be used with furniture." %}

### AVpos-generator script
When placed into a prim this script will output text for a basic notecard listing all the animations contained in the prim, saving the need to manually type animation names. This is not normally used but if you are using a large number of poses this may be more efficient than adding one pose at a time via AVsitter's menu-making system or manual notecard entry.

### AVpos-shifter script
A helpful utility for shifting all positions & rotations in an AVpos notecard by a given amount (e.g. moving all poses 1m to the left) or for moving a setup to a child prim while keeping the positions the same. Also alters positions of props. Full instructions are given when this script is dropped into a prim.

### Anim-perm-checker script
Most animation vendors in SL require that you set permissions to either NO-COPY or NO-TRANSFER for NEXT_OWNER. Drop this script into a prim and it will give a warning in chat for any animations that are set to COPY-TRANSFER.

### Missing-anim-finder script
Drop this script into a prim and it will read through your AVpos notecard and give a warning in chat for any animations that are either missing or not used in the notecard. Also gives the option to delete any animations that are not used.

### MLP-converter script
When placed inside a prim that contains an MLP setup, this script will read through all notecards in the prim that start with .MENUITEMS or .POSITIONS (the standard names for MLP notecards) and generate text in chat. The text can then be pasted into an AVpos notecard. Only MLP's POSE lines will be converted, so you must manually add your MENU & TOMENU lines by [editing the notecard](/avsitter2_avpos.html). Props and facial expressions are not converted by this script.

{% include important.html content="When using the MLP-converter script you can enter a position vector in the prim description e.g. &lt;0,0,0.5&gt; and this will offset the converter's position results by that amount." %}

Follow this step by step guide for more details: [MLP-converter step-by-step guide](avsitter2_StepByStepGuides_MLPconverter.html)

{% include links.html %}
