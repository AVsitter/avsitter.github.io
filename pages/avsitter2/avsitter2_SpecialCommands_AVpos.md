---
title: Special Commands - AVpos
keywords: AVsitter2
sidebar: avsitter2_sidebar
permalink: avsitter2_SpecialCommands_AVpos.html
folder: avsitter2
---

# Special Commands - AVpos

This page is devoted to explaining a few special commands that can be included in the `AVpos` notecard. It's important to note that these commands are not dumped by the `[DUMP]` utility, so we have to manually add them at the top of the `AVpos` notecard.

## HELPER

We can use the AVsitter1 style helper objects by placing `HELPER 1` at the top of the `AVpos` notecard.

With the AVsitter1 style helper objects, you stand up and sit on the actual helpers. The additional permission requests can make it more tedious but it gives instantaneous feedback while positioning the helper objects.

_Original discussion can be found at [https://avsitter.com/qa/49](https://avsitter.com/qa/49)_

## KFM

If you place `KFM 1` at the top of all `AVpos` notecards in the object, it will tell the scripts to expect the use of [llSetKeyframedMotion()](http://wiki.secondlife.com/wiki/LlSetKeyframedMotion) (e.g. for rocking chair or swaying raft, etc). This was added in version `2.01-08`

With this command, Key Framed Motion will be paused momentarily when avatars change pose. The Key Framed Motion will then immediately be resumed.

---

Essentially the scripts are doing as advised on the [SL wiki](http://wiki.secondlife.com/wiki/LlSetKeyframedMotion):

```
llSetKeyframedMotion([],[KFM_COMMAND, KFM_CMD_PAUSE]);
//modify prim positions here
llSetKeyframedMotion([],[KFM_COMMAND, KFM_CMD_PLAY]);
```

We still find [llSetKeyframedMotion()](http://wiki.secondlife.com/wiki/LlSetKeyframedMotion) itself rather buggy and unpredictable. Many residents have filed JIRA reports about problems with [llSetKeyframedMotion()](http://wiki.secondlife.com/wiki/LlSetKeyframedMotion). Also see: [https://avsitter.com/qa/130](https://avsitter.com/qa/130).

NOTE: AVsitter scripts have no way to know if the motion was paused, and will always resume it with [KFM_CMD_PLAY](http://wiki.secondlife.com/wiki/KFM_CMD_PLAY) when the pose is changed. As changing a pose will restart the motion, it may be best if your script completely removes (empties) any Key Framed Motion when the motion is supposed to be stopped, rather than simply pausing it.

_Original discussion can be found at [https://avsitter.com/qa/259](https://avsitter.com/qa/259)_

## LROT

If you place `LROT 1` at the top of the `AVpos` notecard in the object, this will cause the positioning buttons to work relative to the root prim. If the sitter script is in a child prim, it will also be relative to root prim. This helps in cases like:

_Making a vehicle, and using AVsitter to adjust the position of the pilot relative to the vehicle, when the vehicle is at a 45 degree angle, "X+" moves the avatar towards sim-east, instead of vehicle-forward._

Using `LROT 1` this is solved.

_Original discussion can be found at [https://avsitter.com/qa/260](https://avsitter.com/qa/260)_

## WARN

The special command `WARN` is used to control if certain warning messages will show or not.

### WARN 0

In Second Life, less prims than sitting avatars can result in SL's `"No room to sit here"` error when furniture is used within the 'bounding box' of another prim. e.g. a sim-surround landscape sculpty or mesh house. To help prevent people going into that problem unaware, AVsitter2 will give you a warning in a dropdown menu if you are not using the safe minimum prims, `"There aren't enough prims for required SitTargets. You must have one prim for each avatar to sit!"`.

You have the option to disable the warning by placing `WARN 0` at the top of the `AVpos` notecard, but then your users are at risk of receiving SL's `"No room to sit here"` error. Instead, it is suggested that you always have a prim count equal to or more than the number of avatars you plan to sit.

The SL 'bug' is discussed on SL's JIRA [SVC-3811](https://jira.secondlife.com/browse/SVC-3811).

AVsitter2 adds all required sit-targets automatically but with AVsitter1 the `SitTarget-Add` script was required when setting up sits for more than one avatar in the main setup prim. Unfortunately many people did not follow those instructions.

**Land Impact vs Prim Count**

Please make sure you don't get _'Prim Count'_ confused with _'Land Impact'_. LI is not the same as 'Prim Count'. 1 prim doesn't quite mean what it used to, since the introduction of mesh. Each prim may influence the overall LI depending on its complexity and other factors. Two linked prims may have an LI value of 1, but they're still two prims. When we talk about the required prim count we refer to these two prims, whether their LI is 1, 2, or higher. The important for AVsitter is that the prim count is greater or equal than the number of planned sitters.

_Original discussion can be found at [https://avsitter.com/qa/47](https://avsitter.com/qa/47)_

### WARN 1

Default value. All warnings are shown by default.

### WARN 2

If you collect a new package (box 2.1-12.04 or later), the `[AV]prop` script has been modified so you can switch off the next-owner permission check for props by typing `WARN 2` at the top of the notecard. Just be aware that setting next-owner perms on props to no-copy or no-transfer will break props if the furniture is transferred.

_Original discussion can be found at [https://avsitter.com/qa/867](https://avsitter.com/qa/867)_