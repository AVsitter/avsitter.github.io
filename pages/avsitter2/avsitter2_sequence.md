---
title: AVsequence&trade;
keywords: sequence
sidebar: avsitter2_sidebar
permalink: avsitter2_sequence.html
folder: avsitter2
---

## AVsequence&trade;

The [AV]sequence script allows for sequencing of poses, sounds and chat text to create a "scene". Each sequence is composed of any number of steps. If the sequence has multiple animations then a menu is given to control the sequence. You can also have sequences  that simply play a sound or some chat, whenever a pose is played.

{% include important.html content="The [AV]sequence script is specifically made for couples or single-sitter setups. It is not suitable for controlling multiple solo sequences playing at the same time within the same setup prim or for playing sequences across separate prims. See the ['built-in' sequencing method](/avsitter2_avpos.html#built-in-animation-sequence) for another option. For Yoga / Tai-Chi / Line Dancing see [here](https://avsitter.com/qa/815) instead." %}

{% include note.html content="The [AV]sequence script can be found in the Plugins [BOX]." %}

### Sequence Basics
To begin creating sequences:

1. Add the [AV]sequence script and [AV]sequence_settings notecard to a prim that already has working poses.
2. Design the structure of your scene by typing sequence commands into the [AV]sequence_settings notecard.

The following is an example [AV]sequence_settings notecard with one sequence, "Lovescene".

```
SEQUENCE Lovescene
PLAY Couples1
WAIT 30
PLAY Couples2
WAIT 25
PLAY Couples3
WAIT 60
LOOP
```

For the above sequence, you'll need to add a matching SEQUENCE line to your [AVpos](/avsitter2_avpos.html) notecard. e.g.

	SEQUENCE Lovescene

Alternately, make sure your [AVpos](/avsitter2_avpos.html) notecard has a POSE or SYNC that matches the sequence name. e.g.

	SYNC Lovescene|<animation_filename>

{% include note.html content="Sequences in the [AV]sequence_settings notecard are triggered by [SEQUENCE](/avsitter2_avpos.html#sequence), [POSE](/avsitter2_avpos.html#pose) or [SYNC](/avsitter2_avpos.html#sync) in the AVpos notecard." %}

{% include important.html content="For full sequence examples see the [examples section](/avsitter2_sequence.html#sequence-examples) further down this page." %}

{% include tip.html content="Be sure to examine the sequence furniture examples provided in the AVsitter Examples [BOX]." %}

## Sequence Commands
This section outlines each of the notecard commands you can use in the [AV]sequence_settings notecard.

### SEQUENCE
Placed at the start of a new sequence. The name must match the name of a [SEQUENCE](/avsitter2_avpos.html#sequence), [POSE](/avsitter2_avpos.html#pose) or [SYNC](/avsitter2_avpos.html#sync) line in the AVpos notecard.

e.g. in your [AV]sequence_settings notecard:

	SEQUENCE Lovescene

### PLAY
Plays a [POSE](/avsitter2_avpos.html#pose) or [SYNC](/avsitter2_avpos.html#sync) that is defined in your AVpos notecard. It should refer to the menu name you have given your pose, not the animation file name.

e.g.

	PLAY Couples1

### WAIT
Wait for a given time, in seconds. Use this command after the PLAY command, so that a pose is played for the desired duration.

e.g.

	WAIT 5

Using WAIT 0 will cause it to wait until the user manually presses the forward button. e.g.

	WAIT 0

{% include note.html content="If PLAY and WAIT are <ins>both</ins> used in a sequence that is triggered by a SEQUENCE line in the AVpos notecard, the user will be given a menu to control the sequence. Otherwise, the main animation menu is returned as soon as the sequence is selected." %}

### SAY / WHISPER
Say or whisper some text in chat. Hearing range is 20m for say, and 5m for whisper. e.g.

	SAY Everybody raises their glass!

You can use /SITTER# to insert the first name of the avatar on a SITTER. e.g.

	WHISPER /0 takes /1 by the hand.

### LOOP
The sequence will repeat when the end is reached.

When placed at the end of the sequence, the entire sequence will repeat. e.g.

```
SEQUENCE Lovescene
PLAY Couples1
WAIT 30
PLAY Couples2
WAIT 30
PLAY Couples3
WAIT 30
LOOP
```
When placed elsewhere, only the steps that come afterwards will be repeated. e.g.

```
SEQUENCE Lovescene
PLAY Couples1
WAIT 30
LOOP
PLAY Couples2
WAIT 30
PLAY Couples3
WAIT 30
```

### SOUND
Plays a sound file from the prim's inventory. The format is SOUND &lt;sound_file&gt;|&lt;volume&gt;. e.g.

	SOUND giggle|0.5

You can also specify a sound by its UUID. e.g.

	SOUND 71a2b035-8a33-9cb3-e71b-895b515d119f|1

Here's an example of playing a different sound with each pose:

```
SEQUENCE poseA
SOUND sound1|1

SEQUENCE poseB
SOUND sound2|1

SEQUENCE poseC
SOUND sound3|1

SEQUENCE poseD
SOUND sound4|1
```

You can play a whole song by separating SOUND lines with WAIT. e.g.

```
SEQUENCE Song
SOUND Mozart-1|1
WAIT 9.8
SOUND Mozart-2|1
WAIT 9.8
SOUND Mozart-3|1
WAIT 9.8
SOUND Mozart-4|1
WAIT 9.8
LOOP
```

Sound clips that make up a song may fit together better if the WAIT between them is a bit less than their actual length, e.g. if your sounds are 10 seconds long (SL's maximum) they may join together better if the WAIT is set to WAIT 9.8 rather than WAIT 10, as in the example above.

SL won't always play sounds on time unless sounds are pre-loaded to the avatar's viewer. The sequence script will automatically pre-load sounds if there is a WAIT of at least 2 seconds above the SOUND line. To ensure pre-loading of the first sound in the song example above, we could add a new line "WAIT 2" above the first sound.

To give users an option to switch sounds off, add an [ADJUST](/avsitter2_avpos.html#adjust) command to your AVpos notecard, using link message 90205. e.g: 

	ADJUST [SOUND]|90205

{% include tip.html content="Be sure to examine the Piano example provided in the AVsitter Examples [BOX]." %}

### DEBUG
Can assist with debugging your sequences by whispering sequence steps to chat.

	DEBUG 0

The default. No sequence information will be sent to chat.

	DEBUG 1

Will whisper in chat when sequences are started and stopped.

	DEBUG 2

All steps of a sequence will be whispered in chat.

## Sequence Examples

### [AV]sequence_settings notecard

```
SEQUENCE Dance
SOUND dance_music|1

SEQUENCE Hug
WHISPER /0 lovingly hugs /1.
WAIT 10
WHISPER /1 Smiles...

SEQUENCE Kiss
SAY /0 kisses /1 softly...
SOUND de655524-25f5-bb44-151e-e54ff2cef6df|1

SEQUENCE Lovescene1
PLAY Couples1
WAIT 20
PLAY Couples2
WAIT 20
PLAY Couples3
WAIT 20
LOOP

SEQUENCE Lovescene2
PLAY Couples4
WAIT 25
PLAY Couples5
WAIT 25
LOOP

SEQUENCE Song
SOUND Mozart-1|1
WAIT 9.8
SOUND Mozart-2|1
WAIT 9.8
SOUND Mozart-3|1
WAIT 9.8
SOUND Mozart-4|1
WAIT 9.8
LOOP
```

### AVpos notecard

```
SITTER 0

TOMENU Solo
TOMENU Couples
TOMENU Sequences
TOMENU Music

MENU Solo
POSE Sit1|animation1
POSE Sit2|animation2

MENU Couples
SYNC Dance|dance_F
SYNC Hug|hug_F
SYNC Kiss|kiss_F
SYNC Couples1|couples1_F
SYNC Couples2|couples2_F
SYNC Couples3|couples3_F
SYNC Couples4|couples4_F
SYNC Couples5|couples5_F

MENU Sequences
SEQUENCE Lovescene1
SEQUENCE Lovescene2

MENU Music
SEQUENCE Song

SITTER 1

TOMENU Solo
TOMENU Couples
TOMENU Sequences

MENU Solo
POSE Sit1|animation1
POSE Sit2|animation2

MENU Couples
SYNC Dance|dance_M
SYNC Hug|hug_M
SYNC Kiss|kiss_M
SYNC Couples1|couples1_M
SYNC Couples2|couples2_M
SYNC Couples3|couples3_M
SYNC Couples4|couples4_M
SYNC Couples5|couples5_M

MENU Sequences
SEQUENCE Lovescene1
SEQUENCE Lovescene2
```

### Hiding Poses
If you don't want individual poses shown in the menu (e.g. because they are part of a sequence) then you can hide them by placing them in a [MENU](/avsitter2_avpos.html#menu) that has no corresponding [TOMENU](/avsitter2_avpos.html#tomenu) in the AVpos notecard, such as MENU HIDDEN. e.g:

```
MENU HIDDEN
SYNC Couples1|couples1_M
SYNC Couples2|couples2_M
SYNC Couples3|couples3_M
```

{% include links.html %}
