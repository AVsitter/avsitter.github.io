---
title:  "Show/Hide Prim by Sit"
permalink: avsitter2_lsl_example_show_and_hide_prim_by_sit.html
---

```js
/******************************************************************
* This example will hide a prim whenever an avatar is sitting anywhere on the object.
* Place this script into the prim you want to make invisible.
* Will hide the prim whenever an avatar is sitting. Just swap the llSetAlpha() lines to do the opposite!
******************************************************************/

default{
    changed(integer change){
        if(change & CHANGED_LINK){
            // if no avatars sitting
            if(llGetAgentSize(llGetLinkKey(llGetNumberOfPrims()))==ZERO_VECTOR){
                //make prim visible
                llSetAlpha(1,ALL_SIDES);
                llSetLinkPrimitiveParamsFast(LINK_THIS, [PRIM_GLTF_BASE_COLOR, ALL_SIDES, "", "", "", "", "", "", "", "", ""]);
            }
            // if avatars are sitting
            else{
                //make prim invisible
                llSetAlpha(0,ALL_SIDES);
                llSetLinkPrimitiveParamsFast(LINK_THIS, [PRIM_GLTF_BASE_COLOR, ALL_SIDES, "", "", "", "", "", 0.0, PRIM_GLTF_ALPHA_MODE_MASK, 1.0, ""]);
            }
        }
    }
}
```
