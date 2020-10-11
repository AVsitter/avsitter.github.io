# The [AV]LockMeister plugin

LockMeister provides us with functionality to make our furniture emit particles towards specific points of the cuffs, collar, etc. This plugin implements LockMeister in an AVsitter setup (props are not supported yet). We need to follow these steps in order to make the plugin work.

- Which is the SITTER that uses the LockMeister enabled cuffs, etc.? If, for example, this is SITTER 2, we change this line of the code:

```
integer SITTER = 0;
```

to this one:

```
integer SITTER = 2;
```

**NOTE**: If there are several sitters needing to use this plugin, we will use one script per avatar, with the right number in the `integer SITTER = 0;` line.

- The second step is defining which poses require LockMeister enabled attachments. We have to locate the `list POSES` line and add our poses following this format:

```
"pose name 1 in the menu", "attachment's destination point,prim name in engine,attachment's destination point,prim name in engine, ...",
"pose name 2 in the menu", "attachment's destination point,prim name in engine,attachment's destination point,prim name in engine, ...",
...
"pose name N in the menu", "attachment's destination point,prim name in engine,attachment's destination point,prim name in engine, ..."
```

Notice how the last line of the POSES list does not end with a comma (,) at the end. If the last line of the POSES list has a comma, the compiler will issue a Syntax Error.

See the [mooring points list page](http://wiki.secondlife.com/wiki/LSL_Protocol/LockMeister_System#Complete_List_of_Mooring_Points) for an exhaustive list of all the destination points that we can use.

- The third step (optional) is changing the value of PSYS_SRC_TEXTURE with our own texture UUID, if we have a different texture to use. This is very important: if the texture license does not allow for the texture to be given away, then we can't use its texture UUID in the script, for the script has to remain full perms.

**IMPORTANT**: The user has to have the cuffs/etc. attached before the LockMeister associated poses play. Inspect the example object for a set of LockMeister enabled cuffs.
