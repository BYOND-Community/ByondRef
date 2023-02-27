

 winexists proc
----------------




**See also:** 


[winclone proc](#/proc/winclone) 

[winget proc](#/proc/winget) 

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[type parameter (skin)](#/{skin}/param/type) 








**See also:** 

**See also:**

[winclone proc](#/proc/winclone) 

[winget proc](#/proc/winget) 

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[type parameter (skin)](#/{skin}/param/type) 






[winclone proc](#/proc/winclone)

[winget proc](#/proc/winget) 

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[type parameter (skin)](#/{skin}/param/type) 





[winget proc](#/proc/winget)

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[type parameter (skin)](#/{skin}/param/type) 




[winset proc](#/proc/winset)

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 

[type parameter (skin)](#/{skin}/param/type) 



[winshow proc](#/proc/winshow)

[User interface skins](#/{skin}) 

[type parameter (skin)](#/{skin}/param/type) 


[User interface skins](#/{skin})

[type parameter (skin)](#/{skin}/param/type) 

[type parameter (skin)](#/{skin}/param/type)


**Format:** 


 winexists(player, control\_id)
 


**Format:** 

**Format:**

 winexists(player, control\_id)



**Args:** 


 player: A mob or client.
 
 control\_id: The unique ID of a control in the player's skin.
 



**Args:** 

**Args:**

 player: A mob or client.
 
 control\_id: The unique ID of a control in the player's skin.
 


 control\_id: The unique ID of a control in the player's skin.


 Tells if a control exists and if so, what type it is. The return value is
an empty string if the control does not exist, but otherwise it is the type
of control.




 This proc will not tell you if a control has been defined in the skin file
but is not in use yet.




 Because the client must be contacted to get this information, winexists()
will sleep the current proc.





---


