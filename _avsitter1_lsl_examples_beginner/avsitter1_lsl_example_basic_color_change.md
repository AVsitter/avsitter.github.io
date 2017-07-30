---
title:  "Basic Color Change"
permalink: avsitter1_lsl_example_basic_color_change.html
---

```js
/******************************************************************
* This AVsitter™ example will change color when a BUTTON is selected.
* Your AVpos notecard should have buttons for each color e.g.
*
* BUTTON Red|0
* BUTTON White|0
* BUTTON Blue|0
*
* This is a basic example to show concept only.
* If you need custom texture change you should contact your scripter.
******************************************************************/

list  COLOR_NAMES = ["Red","White","Blue"];
list  COLOR_VECTORS = [<1,0,0>,<1,1,1>,<0,0,1>];

default{
        link_message(integer sender, integer num, string msg, key id){
                integer index = llListFindList(COLOR_NAMES,[msg]);
                if(index!=-1){
                        llSetColor(llList2Vector(COLOR_VECTORS,index),ALL_SIDES);
                        llMessageLinked(LINK_SET,90005,"",id);//return menu
                }
        }
}
```
