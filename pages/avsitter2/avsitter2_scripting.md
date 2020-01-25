---
title: LSL Scripting
keywords: AVsitter2
sidebar: avsitter2_sidebar
permalink: avsitter2_scripting.html
---

## LSL Scripting

AVsitter allows creators to trigger animations with their own scripts through "Link Messages" and provides the ability to add [BUTTONS](/avsitter2_avpos.html#button) to menus that send user-defined Link Messages to custom scripts. The examples below are intended only as examples, and to use them correctly you first need to have a decent knowledge of [LSL scripting](http://wiki.secondlife.com/wiki/LSL_Portal).

{% include warning.html content="Don't use this section without a knowledge of [LSL scripting](http://wiki.secondlife.com/wiki/LSL_Portal). If you do not have a knowledge of scripting then please consult your own scripter." %}

{% include important.html content="AVsitter uses Link Messages in the range 90000-90500." %}

{% include note.html content="More scripting info can be found under the 'scripting' tag on the [AVsitter Q&A](https://avsitter.com/qa/tag/scripting) archive." %}

### Link Messages to Send

#### Message 90000

Start a pose. The pose must already be in a SITTER's menu for it to play.

Leaving the key field blank will target all SITTERs. e.g.

    llMessageLinked(LINK_SET, 90000, "Cuddle", "");

If the key is an avatar UUID, it will target only that avatar. e.g.

    llMessageLinked(LINK_SET, 90000, "Sleep", <avatar_uuid>);

If the key is an integer, it will target only that SITTER #. e.g.

    llMessageLinked(LINK_SET, 90000, "Eat", "0");

#### Message 90005

Give menu. Sent with a sitting avatar's UUID this will give the animation menu to them. e.g.

    llMessageLinked(LINK_SET, 90005, "", <avatar_uuid>);

If the string includes a [MENU](/avsitter2_avpos.html#menu) name then it will bring up that specific submenu ([more info](https://avsitter.com/qa/761)). e.g.

    llMessageLinked(LINK_SET, 90005, "My Submenu", <avatar_uuid>);

If using [AVcontrol](/avsitter2_control.html), you can send the controlling avatar's UUID and the sitting avatar's UUID, separated by the pipe (`|`) character. e.g.

    llMessageLinked(LINK_SET, 90005, "", <controller_uuid>|<sitter_uuid>);

This will give the menu of &lt;sitter_uuid&gt; to &lt;controller_uuid&gt;.

#### Message 90004

Same as 90005 but sends the avatar back to the top level of the menu. e.g.

    llMessageLinked(LINK_SET, 90004, "", <avatar_uuid>);

#### Message 90030

Swap two sitters within a setup prim. e.g.

    llMessageLinked(LINK_THIS, 90030, "0", "1");

The above will swap sitters 0 & 1.

This link message can be achieved directly with a [BUTTON](/avsitter2_avpos.html#button). i.e.

    BUTTON SWAP F|90030|0|1

Also see the [SWAP notecard command](/avsitter2_avpos.html#swap).

### Link Messages to Receive

#### Message 90060

Sent when an avatar sits. The string field includes the SITTER # and the key field includes the avatar UUID e.g.

```js
default
{
    link_message(integer sender, integer num, string msg, key id)
    {
        if(num == 90060)
        {
            llSay(0, "Welcome, " + llKey2Name(id));
        }
    }
}
```

#### Message 90065

Sent when an avatar stands. The string field includes the SITTER # and the key field includes the avatar UUID e.g.

```js
default
{
    link_message(integer sender, integer num, string msg, key id)
    {
        if(num == 90065)
        {
            llSay(0, "Goodbye, " + llKey2Name(id));
        }
    }
}
```

#### Message 90045

Sent whenever a pose is played. The key field will include the UUID of the avatar. The string field includes several pieces of information each separated by the pipe (`|`) character. See notes in the example below.

```js
default
{
    link_message(integer sender, integer num, string msg, key id)
    {
        if(num == 90045)
        {
            // The avatar UUID
            key AVATAR_UUID = id;

            // Extract the data into a list
            list data = llParseStringKeepNulls(msg, ["|"], []);

            // The SITTER# the pose is playing for
            integer SITTER_NUMBER = (integer)llList2String(data, 0);

            // The name of the pose
            string POSE_NAME = llList2String(data, 1);

            // The animation file
            string ANIM_FILE = llList2String(data, 2);

            // The SET#
            integer SET = (integer)llList2String(data, 3);

            // A list of UUIDs of all sitting avatars separated by the ( @ ) character
            list ALL_SITTERS = llParseStringKeepNulls(llList2String(data, 4), ["@"], []);

            // The name the SYNC pose the avatar is leaving
            string OLD_SYNC_NAME = llList2String(data, 5);

            // TRUE if the pose is a SYNC pose
            integer IS_SYNC = (integer)llList2String(data, 6);
        }
    }
}
```

#### Message 90050

Sent when a pose is manually selected from the menu. The key field will include the UUID of the avatar. The string field includes the SITTER #, pose name and SET #, separated by the pipe (`|`) character (to separate this information, llParseStringKeepNulls(); is used). Here is an example of using this link message:

```js
default
{
    link_message(integer sender, integer num, string msg, key id)
    {
        if(num == 90050)
        {
            key AVATAR_UUID = id;
            list data = llParseStringKeepNulls(msg,["|"], []);
            string SITTER_NUMBER = llList2String(data, 0);
            string POSE_NAME = llList2String(data, 1);
            string SET = llList2String(data, 2);
        }
    }
}
```
{% include note.html content="90050 is only sent when a pose is manually chosen from the menu. Actions based on which pose is playing should usually use 90045 instead." %}

#### Message 90051

Sent when a sub-[MENU](/avsitter2_avpos.html#menu) is manually selected. Data is the same format as [90050](/avsitter2_scripting.html#message-90050) ([more info](https://avsitter.com/qa/760/)).

## Script Examples

See the following pages for AVsitter2 script examples:

- [LSL Examples (Beginner)](avsitter2_lsl_examples_beginner.html)
- [LSL Examples (Advanced)](avsitter2_lsl_examples_advanced.html)

{% include note.html content="Advanced scripters can [check here for the complete list of messages](https://github.com/AVsitter/AVsitter/blob/master/AVsitter2/avsitter2_link_message_reference.md). You may need to consult the AVsitter source code about what some messages do specifically. Keep in mind that the messages listed in there may change without warning." %}

{% include links.html %}
