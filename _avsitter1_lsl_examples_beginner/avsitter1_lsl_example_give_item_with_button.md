---
title:  "Button Gives Item"
permalink: avsitter1_lsl_example_give_item_with_button.html
---

```js
/******************************************************************
* This AVsitter™ example will give the object "Coffee Cup" to the avatar
* who clicks the button "Coffee" from the menu
* Place the script in any prim in the object with an object named "Coffee Cup"
* You will need a line in the AVpos notecard to create the Button:
* e.g. "BUTTON Coffee|0"
******************************************************************/
default{
    link_message(integer sender, integer num, string msg, key id){
        if(msg=="Coffee"){
            llMessageLinked(LINK_SET,90005,"",id); //optional to give the person the menu
            llSleep(2); //a pause
            llGiveInventory(id,"Coffee Cup");
        }
    }
}
```
