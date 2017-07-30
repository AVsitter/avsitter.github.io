---
title:  "Show/Hide Prim by SitTarget"
permalink: avsitter2_lsl_example_show_and_hide_prim_by_sittarget.html
---

```js
/******************************************************************
* This example will hide a prim whenever an avatar is sitting on the prim the script is in.
* Place this script into the prim you want to make invisible.
******************************************************************/

default{
	changed(integer change){
		if(change & CHANGED_LINK){
			if(llAvatarOnSitTarget() == NULL_KEY){
				llSetAlpha(1,ALL_SIDES);//visible
			}
			else{
				llSetAlpha(0,ALL_SIDES);//invisible	
			}
		}
	}
}
```