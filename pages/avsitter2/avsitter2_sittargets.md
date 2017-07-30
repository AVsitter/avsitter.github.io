---
title: About SitTargets
keywords: AVsitter2
sidebar: avsitter2_sidebar
permalink: avsitter2_sittargets.html
folder: avsitter2
---

## About SitTargets

To sit on an object in SL, the object must have an available SitTarget. Each prim in an object can only have one SitTarget and when an avatar sits on a prim, the avatar will occupy that SitTarget. AVsitter's default is to assign avatars to SITTERs in the order they sit. The first avatar to sit will be assigned to SITTER 0 and the second avatar to sit will be assigned to SITTER 1.

{% include note.html content="An [AV]sit (A+B) pair of scripts defines a SITTER, which is the seat and menu for one avatar." %}

{% include note.html content="For most setups, AVsitter automatically assigns SitTargets as required. You only need to understand this section if you have <a href='/avsitter2_home.html#multiple-setups'>Multiple Setups</a> in your furniture, or if you want to allow avatars to target a certain prim to sit on a specific SITTER." %}

{% include warning.html content="Your furniture must <i>always</i> have a prim count greater than or equal to the number of avatars you plan on sitting." %}

## Assigning SitTargets (special/advanced only)
AVsitter's default is to assign avatars to SITTERs in the order they sit, but you can override it:

<ul>
<li/>If you want to allow avatars to target a specific SITTER when they sit on a certain prim (e.g. cushion).
<li/>When your object contains multiple setup prims that include at least one couples setup.
<li/>To reserve the SitTarget on a certain prim for use by another script (e.g. vehicle's driver script).
</ul>

AVsitter will assign SitTargets to prims using the following method:

<ul>
<li/>If there is only one SITTER in the prim, AVsitter assigns the SitTarget to that prim.
<li/>If there is more than one SITTER in the prim (e.g. couples), AVsitter assigns SitTargets starting with the root prim, followed by prim 2, 3, etc of the furniture...
</ul>

To override the default behavior:

<ol>
<li/>Assign <a href="/avsitter2_avpos.html#set">a SET #</a> in the AVpos notecard.

<li/>Assign each SITTER to a prim by typing the SET # and SITTER # into the description of the prim you want to assign that SITTER to, separated by a dash (-). e.g: 

<ul>
<li/>To assign the SitTarget for SET 0, SITTER 0 to a prim, type 0-0 into the description of that prim.
<li/>To assign the SitTarget for SET 0, SITTER 1 to a prim, type 0-1 into the description of that prim.
<li/>To assign the SitTarget for SET 1, SITTER 1 to a prim, type 1-1 into the description of that prim.
</ul>

note: You must choose prims that are <b>distinctly separate and obvious places</b> for an avatar to sit.

<li/>Repeat for all setups in the furniture that are for more than one avatar.

<li/>Unlink and re-link the object or reset scripts for your changes to take effect.
</ol>

{% include important.html content="See Examples #02b, #04 & #10a in the AVsitter Examples [BOX] (separate prims are assigned to each SITTER)." %}

{% include important.html content="If you assign SitTargets or SET #'s you should do so for all SITTERS in every setup that is for more than one avatar." %}

{% include note.html content="With the [AV]adjuster script in the prim, you can type <b>/5 targets</b> in chat to briefly show the SitTargets in hovertext." %}

{% include important.html content="If you need to use the prim description for another script, you can place the AVsitter bit after a #. e.g. <b>tablecloth#0-0</b>." %}

<br>
<b>Assigning SitTargets Video</b>

<iframe height="349" src="https://www.youtube.com/embed/RYqGKGk21D8?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>

### SitTargets and Multiple Setups
If you have <a href="/avsitter2_home.html#multiple-setups">Multiple Setups</a> in your furniture then you must <a href="/avsitter2_avpos.html#set">assign a unique SET #</a> to each setup that is for more than one avatar. e.g. If you have 2 separate couples setups in the same furniture, type SET 0 into the notecard of one and SET 1 into the notecard of the other. You would then need to <a href="/avsitter2_sittargets.html#assigning-sittargets-specialadvanced-only">Assign a SitTarget</a> in prim descriptions for each SITTER in those setups.

{% include important.html content="See AVsitter Example#09 in the AVsitter Examples [BOX] (example shows a couch with couples and 3 singles prims)." %}

{% include important.html content="See AVsitter Example#10b in the AVsitter Examples [BOX] (example shows a couch with multiple couples prims)." %}

<br>
<b>SitTargets and Multiple Setups Video</b>

<iframe height="349" src="https://www.youtube.com/embed/KilhfAQsrY4?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>

### Reserving SitTargets
AVsitter places and removes SitTargets automatically throughout the object, but you might want to override this:

<ul>
<li/>For a vehicle's driver seat <i>which has its own animations</i> in the vehicle script.
<li/>If you are using a different sit script in one of the prims.
</ul>

To reserve the SitTarget of a specific prim, use -1 in that prim's description. Remember to re-link the object for changes to take effect.

After adding -1 to a prim's description you should reset your own scripts inside the prim, to ensure those scripts replace their own SitTargets.

If your use of AVsitter includes any prims for multiple sitters then you will also need to follow the instructions for <a href="/avsitter2_sittargets.html#sittargets-and-multiple-setups">SitTargets and Multiple Setups</a> as described above (assigning a SET # to each setup and assigning the SitTargets in prim descriptions).

{% include important.html content="See the vehicle setup examples provided in the AVsitter Examples [BOX]." %}

As an alternate to placing -1 in the prim description you can add a custom script to the prim that uses the 90150 link message to replace the SitTarget in the prim when required. e.g:

```js
default{
	link_message(integer sender, integer num, string msg, key id){
		if(num==90150){
			llSitTarget(<0,0,0.1>,ZERO_ROTATION);	
		}
	}
}
```

<b>Reserving SitTargets Video</b>

<iframe height="349" src="https://www.youtube.com/embed/zRD_Uwenh6c?rel=0" frameborder="0" width="560" allowfullscreen=""></iframe>

{% include links.html %}
