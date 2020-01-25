---
title:  "Pose Gives Item"
permalink: avsitter1_lsl_example_give_item_with_pose.html
---

```js
/******************************************************************
* This AVsitter™ example will give items with a pose
* Note that the "S:" is required to detect the SYNC pose
******************************************************************/
default{
    link_message(integer sender, integer num, string msg, key id){
        if(num==90055){
            llSleep(2); //a pause
            if(msg=="Drink"){
                llGiveInventory(id,"Coffee Cup");
            }
            else if(msg=="Brush"){
                llGiveInventory(id,"Hair Brush");
            }
        }
    }
}
```
