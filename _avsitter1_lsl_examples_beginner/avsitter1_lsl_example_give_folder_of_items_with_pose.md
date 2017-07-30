---
title:  "Pose Gives Folder"
permalink: avsitter1_lsl_example_give_folder_of_items_with_pose.html
---

```js
/******************************************************************
* This AVsitter™ example will give items in a folder with a pose
* Note that the "S:" is required at start of the posename to detect a SYNC pose
******************************************************************/
string posename = "PaintNails";
list items = ["Bottle","Brush"];
string foldername = "NailPolish Folder";

default{
    link_message(integer sender, integer num, string msg, key id){
        if(num==90055){
            if(msg==posename){
                llSleep(2);
                llGiveInventoryList(id,foldername,items);
            }
        }
    }
}
```
