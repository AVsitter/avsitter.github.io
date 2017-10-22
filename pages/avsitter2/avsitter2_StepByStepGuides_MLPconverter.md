---
title: Step by Step Guide - MLP Converter
keywords: AVsitter2
sidebar: avsitter2_sidebar
permalink: avsitter2_StepByStepGuides_MLPconverter.html
folder: avsitter2
---

### MLP-converter script

MLP (Multi-Love Pose) is a pose engine similar to AVsitter that uses pose balls. It was the choice in the past for many engines, but it has now become obsolete. We may have engines made in MLP that we want to convert to AVsitter. This tool will help with the process.

Before detailing the process, it's important to make clear that this tool **only** converts the POSE lines. Props, facial expressions, and others like sequences and swaps will not be converted by this script. You also must manually add your MENU & TOMENU lines by <a href="/avsitter2_avpos.html">editing the `AVpos` notecard</a>.

Let's now detail the process:

- Rez your MLP-powered object.
- Delete all the MLP scripts from it. Delete the `~ball` object.
- Keep (for now) the notecards beginning by `.MENUITEMS` and `.POSITIONS`. Delete all the other MLP notecards like `.PROPS`, `.SEQUENCES`, etc. If you have other scripts, do not delete their configuration notecards, only the MLP-related ones.
- Locate the `MLP-converter` script of your AVsitter distribution (which is inside the `Utilities [BOX]` if you've purchased AVsitter)
- Drop this script in the contents of the prim with the MLP notecards
- Wait a bit. It will read all the `.MENUITEMS` and `.POSITIONS` notecards, and output lines with the POSE lines corresponding to the separate sitters.
- Once it's done, it will remove itself from the object. Copy all the lines it has output into an `AVpos` notecard.
- Follow the instructions for a normal set-up, using the new AVpos notecard, dropping the necessary AVsitter scripts into your object, etc.

Sit on your object. Observe that the positions aren't the same ones you had. Likely, all the problem is that you are showing *below* the item, this is, the Z coordinate isn't correct. Follow these steps to fix it:

- Click the AVsitter menu, click [ADJUST] and then [HELPER]. This rezzes all the helper bars. You need to focus only in the one that moves you.
- Take note of its position. For example, the initial position vector might look like: `<165.19110, 132.34120, 501.60141>`.
- Now drag the bar vertically until you see yourself correctly, and take note of this final position. This might look like `<165.19110, 132.34120, 502.10141>`.
- Stand up from the object and calculate the difference of the initial vector minus the final vector. We obtain, for example: `<0, 0, -0.5>`.
- Write that vector, `<0, 0, -0.5>` in the description of the prim with all the scripts.
- Drop again the `MLP-converter` script and let it do its job.
- Copy all the lines it has output into your existing `AVpos` notecard. Replace it in your object, which will force the scripts to read all the configuration, now corrected.
- When you are satisfied with the result, you may delete the notecards beginning by `.MENUITEMS` and `.POSITIONS`.

Sit again on your object. The position issue is fixed and the description of the prim is free for us to be rewritten if needed by other scripts.

This will not complete everything we must do. Let's insist on this:

- We have to manually redo our menus
- Props must be redone with the AVsitter scripts, and replaced into the object
- Sequences must be redone to suit the format of the `[AV]sequence_settings` notecard
- Facial expressions must be added manually
- etc.

So we work that on our `AVpos` notecard, and we finally obtain the complete engine, ready to work with AVsitter.

{% include important.html content="It's also worth noting that in times of the MLP engines, the first sitter (`SITTER 0` in AVsitter) used to be the male sitter. However, AVsitter engines have evolved so the first sitter, `SITTER 0`, is usually the female sitter. This means that you may need to swap the `SITTER 0` and `SITTER 1` portions of text." %}

{% include links.html %}
