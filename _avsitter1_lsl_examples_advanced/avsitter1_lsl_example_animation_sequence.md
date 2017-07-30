---
title:  "Animation Sequence"
permalink: avsitter1_lsl_example_animation_sequence.html
---

```js
/******************************************************************
 * This AVsitter™ example will start a sequence of animations when a BUTTON is pressed on the menu.
 * Alternately, the sequence can start automatically when a set number of avatars sit (see AVATARS_TRIGGER below).
 * If you have multiple sequences in your furniture you can use one copy of this script for each sequence.
 * The script will stop playing the sequence when any new animation or sequence is selected with the menu.
 * Please read the notes for each setting below.
******************************************************************/

// SEQUENCE_NAME should match the BUTTON name in your AVpos notecard you are using to trigger the sequence.
string SEQUENCE_NAME = "Sequence1";

// SEQUENCE_POSES is the list of POSES you want in the sequence. These should match the menu names you have given the poses, not the animation names. If using a SYNC pose, place "S:" in front of the name.
list SEQUENCE_POSES = ["S:couples1","S:couples2","Sit1","Sit2"];

// SEQUENCE_TIMES lists how long each pose will be played in seconds, and should match the list length of SEQUENCE_POSES.
list SEQUENCE_TIMES = [5,5,5,5];

// SEQUENCE_LINKNUMBER should match the sequence trigger BUTTON's link number (should be the same for all sequences) e.g. BUTTON Sequence1|99
integer SEQUENCE_LINKNUMBER=99;

// REPEAT_SEQUENCE can be set to TRUE or FALSE depending on if you want the sequence to loop back to the beginning.
integer REPEAT_SEQUENCE = TRUE;

// AVATARS_TRIGGER can auto-trigger the sequence when a certain number of avatars are sitting. e.g. AVATARS_TRIGGER = 2;
integer AVATARS_TRIGGER = FALSE;

// VERBOSE simply controls if you want the script to say "Sequence Stopped!" and "Sequence Started!" in local chat.
integer VERBOSE = TRUE;

/******************************************************************
 * DON'T EDIT BELOW THIS UNLESS YOU KNOW WHAT YOU'RE DOING!
******************************************************************/

integer sequence_running;
integer pointer;

start_sequence(){
        if(VERBOSE){
                llWhisper(0,"Sequence '"+SEQUENCE_NAME+"' Started!");
        }
        pointer=0;
        sequence_running=TRUE;
        llSetTimerEvent(0.01);
}

stop_sequence(){
        if(sequence_running){
                pointer=0;
                llSetTimerEvent(0);
                sequence_running=FALSE;
                if(VERBOSE){
                        llWhisper(0,"Sequence '"+SEQUENCE_NAME+"' Stopped!");
                }
        }
}

default{
        link_message(integer sender, integer num, string msg, key id){
                if(num==SEQUENCE_LINKNUMBER && msg==SEQUENCE_NAME){
                        start_sequence();
                }
                else if(num==90055 && llListFindList(SEQUENCE_POSES,[msg])==-1 || num == SEQUENCE_LINKNUMBER){ //stop playing the sequence when any new animation is played. Or when another sequence with the same SEQUENCE_LINKNUMBER is played.
                        if(llGetTime()>1){
                                stop_sequence();
                        }
                }
        }
        changed(integer change){
                if(change & CHANGED_LINK){
                        if (AVATARS_TRIGGER && llGetAgentSize(llGetLinkKey(llGetNumberOfPrims()-AVATARS_TRIGGER+1)) != ZERO_VECTOR){
                                llResetTime();
                                start_sequence();
                        }
                        else{
                                stop_sequence();
                        }
                }
        }
        timer(){
                llMessageLinked(LINK_SET,90000,llList2String(SEQUENCE_POSES,pointer),"");
                llSetTimerEvent(llList2Float(SEQUENCE_TIMES,pointer));
                pointer++;
                if(pointer==llGetListLength(SEQUENCE_POSES)){
                        pointer=0;
                        if(REPEAT_SEQUENCE==FALSE){
                                llSetTimerEvent(0);
                        }
                }
        }
}
```