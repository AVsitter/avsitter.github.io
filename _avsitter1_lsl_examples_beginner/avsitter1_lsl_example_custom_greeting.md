---
title:  "Custom Greeting"
permalink: avsitter1_lsl_example_custom_greeting.html
---

```js
/******************************************************************
* This AVsitter™ example will IM a custom greeting to each new sitter
* Place a single copy in any prim in the object
******************************************************************/
default{
    link_message(integer sender, integer num, string msg, key id){
        if(num==90060){
            llInstantMessage(id,"Welcome!");
        }
        else if(num==90065){
            llInstantMessage(id,"Goodbye!");
        }
    }
}
```
