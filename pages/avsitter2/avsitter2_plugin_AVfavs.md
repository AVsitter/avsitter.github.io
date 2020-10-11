---
title: The AVfavs plugin
keywords: AVsitter2, avfavs
sidebar: avsitter2_sidebar
permalink: avsitter2_plugin_AVfavs.html
folder: Plugins
---

# [AV]favs

`[AV]favs`, available since version 2.2r04, gives the user the ability to manage a list of their favorite poses in an engine. The use is simple: we can add the current pose to our favorites list, delete the current pose, and show a menu to select a pose to play among our favorites (select favorite menu).

It is set up through linked messages, so we need to use either the `BUTTON` or `ADJUST` commands. Below you can see some examples of how to implement the `[AV]favs` plugin.

## Example 1

We want to add all the buttons under a `FAVORITES` submenu. Snippet of the `AVpos` notecard:

```
TOMENU FAVORITES

...

MENU FAVORITES

BUTTON Add Fav|90401
BUTTON Del Fav|90402
BUTTON Favorites...|90403
```

## Example 2

We want to add the add favorite and delete favorite buttons under the `[ADJUST]` menu, and the select favorite menu as a `BUTTON` on the main menu. Snippet of the `AVpos` notecard:

```
ADJUST Add Fav|90401|Del Fav|90402

...

BUTTON Favorites...|90403
```

## Example 3

We want to add all three buttons under the `[ADJUST]` menu. Snippet of the `AVpos` notecard:

```
ADJUST Add Fav|90401|Del Fav|90402|Favorites...|90403
```

Summarizing, these are the message codes the plugin expects:

- 90401: Adds a favorite
- 90402: Deletes a favorite
- 90403: Shows the favorites menu
