---
title:  "Autoplay"
permalink: avsitter1_lsl_example_autoplay.html
---

```js
/******************************************************************
* This AVsitter™ example will auto-play a SYNC pose when 2 avatars sit,
* and automatically play a different POSE when 1 avatar stands up.
* (This is for a two person cuddle chair in mind)
* We'll say for this example that the two animations are as follows:
*            1: a SYNC animation named "Close"
*            2: a POSE called "Sit1"
* Note that the "S:" is required to play the SYNC animation
******************************************************************/
default{
        changed(integer change){
        if(change & CHANGED_LINK){
            integer count = llGetNumberOfPrims();
            while (llGetAgentSize(llGetLinkKey(count)) != ZERO_VECTOR){ // prim is an avatar!
                count--;
            }
            if(llGetNumberOfPrims()-count>1){
                llMessageLinked(LINK_SET,90000,"S:Close","");
            }
            else{
                llMessageLinked(LINK_SET,90000,"Sit1","");
            }
                }
        }
}
```
