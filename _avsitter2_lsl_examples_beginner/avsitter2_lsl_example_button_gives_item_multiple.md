---
title:  "Button Gives Multiple Items"
permalink: avsitter2_lsl_example_button_gives_item_multiple.html
---

```js
/******************************************************************
* This example will give different objects to an avatar who presses different BUTTON in the menu
* You will need a line in the AVpos notecard for each BUTTON
* e.g. BUTTON Coffee|0
******************************************************************/

default{
    link_message(integer sender, integer num, string msg, key id){
        if(msg=="Coffee"){
            llGiveInventory(id,"Coffee Cup");
        }
        else if (msg=="Donut"){
            llGiveInventory(id,"donut");
        }
        else if (msg=="Lunch"){
            llGiveInventory(id,"Lunchbox");
        }
        else if (msg=="Pastry"){
            llGiveInventory(id,"coconut swirl");
        }
    }
}
```