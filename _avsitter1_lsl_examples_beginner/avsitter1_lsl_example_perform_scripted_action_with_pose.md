---
title:  "Perform any Script Action with a Pose"
permalink: avsitter1_lsl_example_perform_scripted_action_with_pose.html
---

```js
/******************************************************************
* This AVsitter™ example will perform actions with specific poses
* Note that the "S:" is required to detect the SYNC pose
******************************************************************/
default{
    link_message(integer sender, integer num, string msg, key id){
        if(num==90055){
            if(msg=="Sit1"){
                llSay(0,"Sit1 selected!");
            }
            else if(msg=="Sit2"){
                llSay(0,"Sit2 selected!");
            }
            else if(msg=="S:Couples1"){
                llSay(0,"Couples1 selected!");
            }
        }
    }
}
```
