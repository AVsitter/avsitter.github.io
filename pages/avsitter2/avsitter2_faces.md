---
title: AVfaces&trade;
keywords: plugin, faces
sidebar: avsitter2_sidebar
permalink: avsitter2_faces.html
folder: avsitter2
---

## AVfaces&trade;

The [AV]faces script allows creators to add facial expressions to AVsitter&trade; furniture. 

{% include important.html content="Facial expressions can be switched off via the [FACES] button in the [ADJUST] menu." %}

### Adding Facial Expressions
To add facial expressions to your furniture, start with the <a href="/avsitter2_home.html#setup">normal setup</a> procedure, then:

<ol>
<li/>Ensure the [AV]helper and [AV]adjuster are in the prim.

<li/>Drop the [AV]faces script into the prim.

<li/>Sit on the furniture, then choose a pose from the menu that will trigger the facial expression.

<li/>Choose [ADJUST] then [HELPER] from the menu, and the [AV]helper stick will rez.

<li/>Choose [NEW] from the menu, then choose [FACE] and select an expression from the list.

<li/>You should see the facial expression playing on your avatar.

<li/>Repeat for each pose you want to give a facial expression.

<li/>When you have finished adding all your facial expressions, click [DUMP] to output your settings into chat.

<li/>Copy-paste the [DUMP] result into your AVpos notecard, replacing the contents of the notecard.
</ol>

{% include note.html content="Facial Expressions are defined separately for each SITTER." %}

### Notecard Commands
Facial expressions added via the [NEW] menu will simply repeat the expression every 1 second. You can edit the notecard to add facial expressions manually or change how they behave.

The format for the notecard is:

	ANIM <trigger_name>|<expression>|<duration>|<expression>|<duration>|<expression>|<duration> ...

&lt;trigger_name&gt; must match the menu name of the pose that you want to trigger the facial expression sequence.

&lt;expression&gt;&#124;&lt;duration&gt; is a facial expression followed by the number of seconds to play it.

For example in the following notecard line:

	ANIM Anim1|express_smile|1

When the "Anim1" pose is selected from the menu the script will play the expression "express_smile" every 1 second.

Another example:

	ANIM Happy|express_laugh_emote|5|express_smile|1|express_wink_emote|2

When the "Happy" pose is selected from the menu the script will play the expression "express_laugh_emote". Then after 5 seconds play "express_smile", then "express_wink_emote", then loop to the start after 2 seconds.

Another example:

	ANIM Sleep|express_smile|1|express_disdain|1

When the "Sleep" pose is selected, this alternates between "express_smile" and "express_disdain" every second. SL does not offer a facial expression for sleeping but combining these animations gives a close approximation.

Usually a sequence will loop, but if a dash ( - ) is entered instead of a duration then the sequence will stop after playing. e.g.

	ANIM Happy|express_laugh_emote|5|express_smile|-

If you want to continually re-apply an expression every second, then begin it's duration with a dash ( - ). e.g:

	ANIM Happy|express_laugh_emote|-5|express_smile|-3

You can use 'none' for the name of an animation file if you need to create a pause. e.g.

	ANIM Happy|express_laugh_emote|-5|none|5

The facial expresssions available in SL include:

	express_afraid_emote, express_anger_emote, express_laugh_emote, express_bored_emote, express_cry_emote, express_embarrassed_emote, express_sad_emote, express_toothsmile, express_smile, express_surprise_emote, express_worry_emote, express_repulsed_emote, express_shrug_emote, express_wink_emote, express_disdain, express_frown, express_kiss, express_open_mouth, express_tongue_out

In addition to SL facial expressions, you can also use any (non looped) animation that is in the furniture. e.g:

	ANIM Cheer|ArmsUp|-

If you want to re-use an ANIM line that is already defined for the same sitter, then simply refer to that line instead of creating a new sequence. Requires box <a href="//avsitter.com/updates">2.1-12.05</a> or later. e.g.:

	ANIM pose1|express_laugh_emote|5|express_smile|1
	...
	ANIM pose2|pose1

{% include note.html content="The full list of internal SL animations can be found <a href='http://wiki.secondlife.com/wiki/Internal_Animations'>here</a>, and examples of the facial expressions <a href='http://wiki.secondlife.com/wiki/File:SL_face_expressions.jpg'>here</a>." %}

{% include important.html content="We suggest a sensible maximum of 3 expressions per ANIM line, to conserve script memory and reduce clutter. Also, scripts can only read the first 255 characters (bytes) per notecard line." %}

{% include tip.html content="For examples that use AVfaces&trade;, see the Plugins Examples [BOX]." %}

{% include important.html content="<a href='https://community.secondlife.com/t5/Featured-News/Introducing-Project-Bento-New-Bones-Added-to-Second-Life-Avatar/ba-p/2987206'>Project Bento</a> is in the works by LL, which may significantly change the way facial animations are used in SL." %}

{% include links.html %}
