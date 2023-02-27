

 stat proc
-----------




**See also:** 


[Stat proc (atom)](#/atom/proc/Stat) 

[Stat proc (client)](#/client/proc/Stat) 

[statpanel proc](#/proc/statpanel) 

[Info control (skin)](#/{skin}/control/info) 






**See also:** 

**See also:**

[Stat proc (atom)](#/atom/proc/Stat) 

[Stat proc (client)](#/client/proc/Stat) 

[statpanel proc](#/proc/statpanel) 

[Info control (skin)](#/{skin}/control/info) 




[Stat proc (atom)](#/atom/proc/Stat)

[Stat proc (client)](#/client/proc/Stat) 

[statpanel proc](#/proc/statpanel) 

[Info control (skin)](#/{skin}/control/info) 



[Stat proc (client)](#/client/proc/Stat)

[statpanel proc](#/proc/statpanel) 

[Info control (skin)](#/{skin}/control/info) 


[statpanel proc](#/proc/statpanel)

[Info control (skin)](#/{skin}/control/info) 

[Info control (skin)](#/{skin}/control/info)


**Format:** 


 stat(Name,Value)
 


**Format:** 

**Format:**

 stat(Name,Value)



**Args:** 


 Name: the name of the stat line
 
 Value: the data to be displayed
 



**Args:** 

**Args:**

 Name: the name of the stat line
 
 Value: the data to be displayed
 


 Value: the data to be displayed


 This is used in a Stat() proc to send a stat line to usr, the person
looking at an object. A stat line has an optional name part which must be
unique for each stat line (or successive calls will replace previous ones).




 The stat line gets appended to the current stat panel. The current panel
may be changed by using statpanel().




 If no name is specified and the value is a list, this is the same as
calling stat on each item in the list. This can be used (in conjunction
with statpanel) to create an inventory panel or something similar.



### 
 Example:



 mob/Stat()
 stat("description",src.desc)
 if(src == usr) stat(src.contents)


 This example displays the mob's description and inventory all in one panel.
The code ensures that only the mob may see his own inventory, but you don't
have to worry about that unless you change client.statobj to something other
than one's own mob.





---


