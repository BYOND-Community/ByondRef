

 winclone proc
---------------




**See also:** 


[winexists proc](#/proc/winexists) 

[winget proc](#/proc/winget) 

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 







**See also:** 

**See also:**

[winexists proc](#/proc/winexists) 

[winget proc](#/proc/winget) 

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 





[winexists proc](#/proc/winexists)

[winget proc](#/proc/winget) 

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 




[winget proc](#/proc/winget)

[winset proc](#/proc/winset) 

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 



[winset proc](#/proc/winset)

[winshow proc](#/proc/winshow) 

[User interface skins](#/{skin}) 


[winshow proc](#/proc/winshow)

[User interface skins](#/{skin}) 

[User interface skins](#/{skin})


**Format:** 


 winclone(player, window\_name, clone\_name)
 


**Format:** 

**Format:**

 winclone(player, window\_name, clone\_name)



**Args:** 


 player: A mob or client.
 
 window\_name: The name of a window, pane, menu, or macro set in the world's skin file.
 
 clone\_name: The name of the new window, pane, menu, or macro set to create.
 




**Args:** 

**Args:**

 player: A mob or client.
 
 window\_name: The name of a window, pane, menu, or macro set in the world's skin file.
 
 clone\_name: The name of the new window, pane, menu, or macro set to create.
 



 window\_name: The name of a window, pane, menu, or macro set in the world's skin file.
 
 clone\_name: The name of the new window, pane, menu, or macro set to create.
 


 clone\_name: The name of the new window, pane, menu, or macro set to create.


 Creates a clone of a window, pane, menu, or macro set that exists in the
world's skin file. The original object as it exists in the skin file (not its
current state) is used as a template to build the clone. The clone will exist
only for the player you choose.



### 
 Example:



 winset(usr, "templatewindow", "clonedwindow")


 If a window is not visible by default, it will have to be shown with
 
 winset()
 
 or
 
 winshow()
 
 . A pane may be shown by using it in a
Child or Tab control. Menus or macros must be assigned to a window with
 
 winset()
 
 before they will work.




 winset()


 winshow()


 winset()


 If window\_name is "window", "pane", "menu", or "macro", and the skin file
does not have a control of that name already, the proc will create a new
control of that type from scratch.



### 
 Example:



 winclone(usr, "menu", "newmenu")
winset(usr, "newmenu\_file", "parent=newmenu;name=File")
winset(usr, "newmenu\_quit", "parent=newmenu\_file;name=Quit;command=.quit")


 A new window is invisible by default. For windows and panes, you should
give them a size with
 
 winset()
 
 before adding any controls so you can
set their anchors properly.




 winset()

### 
 Example:



 // Create the pane
winclone(usr, "pane", "newpane")
// Give it a size so we can figure out where to put controls
winset(usr, "newpane", "size=100x100")
// Add controls
winset(usr, "newpane\_label", \
 "parent=newpane;pos=0,0;size=100x100;anchor1=0,0;anchor2=100,100")
// Put the pane in a child control where it can be seen
winset(usr, "a\_child", "left=newpane")
usr << output("New label", "newpane\_label")


 Once a clone is created, it can be deleted via a
 
 winset()
 
 call:




 winset()

### 
 Example:



 winset(usr, "clonedwindow", "parent=none")



---


