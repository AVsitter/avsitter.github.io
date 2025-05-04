---
title:  "Show/Hide Prim by Button"
permalink: avsitter2_lsl_example_show_and_hide_prim_by_button.html
---

```js
/******************************************************************
* This example will show/hide a prim when a button is pressed in the menu.
* Place this script into the prim you want to make invisible.
*
* You will need a line in the AVpos notecard to create the BUTTON:
* BUTTON Blanket|0
******************************************************************/

string button_name = "Blanket";
integer visible=TRUE;

default {
    state_entry(){
        llSetAlpha(1,ALL_SIDES);//visible
    }
    link_message(integer sender, integer num, string msg, key id){
        if(msg==button_name){
            if(visible){
                llSetAlpha(0,ALL_SIDES);//invisible
                llSetLinkPrimitiveParamsFast(LINK_THIS, [PRIM_GLTF_BASE_COLOR, ALL_SIDES, "", "", "", "", "", 0.0, PRIM_GLTF_ALPHA_MODE_MASK, 1.0, ""]);
            }
            else{
                llSetAlpha(1,ALL_SIDES);//visible
                llSetLinkPrimitiveParamsFast(LINK_THIS, [PRIM_GLTF_BASE_COLOR, ALL_SIDES, "", "", "", "", "", "", "", "", ""]);
            }
            llMessageLinked(LINK_SET,90005,"",id); // give back the menu
            visible=!visible;
        }
    }
}
```
