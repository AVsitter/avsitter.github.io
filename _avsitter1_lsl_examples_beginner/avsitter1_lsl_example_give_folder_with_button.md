---
title:  "Button Gives Folder"
permalink: avsitter1_lsl_example_give_folder_with_button.html
---

```js
/******************************************************************
* This AVsitter™ example will give items in a folder when a button is pressed
* You will need a line in the AVpos notecard to create the Button:
* e.g. "BUTTON Give Items|0"
******************************************************************/
string button = "Give Items";
list items = ["Item1","Item2","Item3"];
string foldername = "Object Folder";

default{
    link_message(integer sender, integer num, string msg, key id){
        if(msg==button){
            llMessageLinked(LINK_SET,90005,"",id); //optional to give the person the menu
            llSleep(2); //a pause
            llGiveInventoryList(id,foldername,items);
        }
    }
}
```
