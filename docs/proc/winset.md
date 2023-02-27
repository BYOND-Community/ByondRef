

 winset proc
-------------




**See also:** 


[winclone proc](#/proc/winclone) 

[winexists proc](#/proc/winexists) 

[winget proc](#/proc/winget) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[parameters (skin)](#/{skin}/param) 








**See also:** 

**See also:**

[winclone proc](#/proc/winclone) 

[winexists proc](#/proc/winexists) 

[winget proc](#/proc/winget) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[parameters (skin)](#/{skin}/param) 






[winclone proc](#/proc/winclone)

[winexists proc](#/proc/winexists) 

[winget proc](#/proc/winget) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[parameters (skin)](#/{skin}/param) 





[winexists proc](#/proc/winexists)

[winget proc](#/proc/winget) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[parameters (skin)](#/{skin}/param) 




[winget proc](#/proc/winget)

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[parameters (skin)](#/{skin}/param) 



[winshow proc](#/proc/winshow)

[User interface skins](#/{skin}) 

[parameters (skin)](#/{skin}/param) 


[User interface skins](#/{skin})

[parameters (skin)](#/{skin}/param) 

[parameters (skin)](#/{skin}/param)


**Format:** 


 winset(player, control\_id, params)
 


**Format:** 

**Format:**

 winset(player, control\_id, params)



**Args:** 


 player: A mob or client.
 
 control\_id: The unique ID of a control in the player's skin.
 
 params: A text string with parameters to set, in the format returned by
 
 list2params()
 
 ;
 *OR* 
 an associative list.
 




**Args:** 

**Args:**

 player: A mob or client.
 
 control\_id: The unique ID of a control in the player's skin.
 
 params: A text string with parameters to set, in the format returned by
 
 list2params()
 
 ;
 *OR* 
 an associative list.
 



 control\_id: The unique ID of a control in the player's skin.
 
 params: A text string with parameters to set, in the format returned by
 
 list2params()
 
 ;
 *OR* 
 an associative list.
 


 params: A text string with parameters to set, in the format returned by
 
 list2params()
 
 ;
 *OR* 
 an associative list.


 list2params()

*OR*

 Sets parameters for a player's skin. The parameter list can be created by
making a list and using
 
 list2params()
 
 , or it can be done manually by
just using a string like
 
 "is-visible=true;text-color=#f00"
 
 . You can
also just use a list directly, which will be passed to
 
 list2params()
 
 internally.




 list2params()


 "is-visible=true;text-color=#f00"


 list2params()


 The
 
 control\_id
 
 can be a window name, or in a
 
 "[window].[control]"
 
 format, or just the control ID as long as it is
unique. In some special cases it can also be null. Another valid form is
 
 ":[type]"
 
 which selects the default control of that type, e.g.
 
 ":map"
 
 for the main map.




 control\_id


 "[window].[control]"


 ":[type]"


 ":map"


 If you want to use a text string that may include spaces, surround the
string with double quotes and escape them using a backslash, e.g.
 
 "text=\"This is some text.\""
 
 . Backslashes can also be used by
preceding them with another backslash. For filenames, use single quotes around
the file. Sometimes escapement may need to go several levels deep; for example
to set up an input control with a default say command, you will need to escape
it twice:




 "text=\"This is some text.\""


> 
>  Desired command:
>  
>  say "
>  
>   
> 
>  Escaped form with quotes:
>  
>  "
>  **say \"** 
>  "
>  
>   
> 
>  Final form:
>  
>  \"say \\\"\"
>  
> 
> 
>  winset(usr, "mainwindow.input", "command=
>  **\"say \\\"\"** 
>  ")
>  
> 
> 
> 
> 



 say "

  


 "
 **say \"** 
 "

**say \"**
  


 \"say \\\"\"



 winset(usr, "mainwindow.input", "command=
 **\"say \\\"\"** 
 ")
 




 winset(usr, "mainwindow.input", "command=
 **\"say \\\"\"** 
 ")

**\"say \\\"\"**

 You can set more than one control's parameters at once by leaving the
 
 control\_id
 
 argument null, and including the control as part of the
parameter list:




 control\_id


 winset(usr, null,\
 "mainwindow.output.background-color=#ffffff;mainwindow.input.background-color=#ffffff")

### 
 Special winsets



 Some "global" winset options will let you change things that affect the
client as a whole, not just specific controls.




 You can reset the skin to its beginning state, removing all
runtime-created controls and windows, by calling
 
 winset(player, null, "reset=true")
 
 .




 winset(player, null, "reset=true")


 Another use for
 
 winset()
 
 is to send commands to the client that
normally can only run from there, like
 
 .profile
 
 or
 
 .quit
 
 . To
do this, leave the
 
 control\_id
 
 argument null, and just use a parameter
called "command":




 winset()


 .profile


 .quit


 control\_id


 obj/quitbutton
 name = "Quit"
 icon = 'buttons.dmi'
 icon\_state = "quit"

 Click()
 winset(usr, null, "command=.quit")



---


