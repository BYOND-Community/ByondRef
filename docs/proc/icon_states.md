

 icon\_states proc
-------------------




**See also:** 


[icons](#/DM/icon) 

[icon\_size var (world)](#/world/var/icon_size) 

[map\_format var (world)](#/world/var/map_format) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 







**See also:** 

**See also:**

[icons](#/DM/icon) 

[icon\_size var (world)](#/world/var/icon_size) 

[map\_format var (world)](#/world/var/map_format) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 





[icons](#/DM/icon)

[icon\_size var (world)](#/world/var/icon_size) 

[map\_format var (world)](#/world/var/map_format) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 




[icon\_size var (world)](#/world/var/icon_size)

[map\_format var (world)](#/world/var/map_format) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 



[map\_format var (world)](#/world/var/map_format)

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 


[Big icons](#/{notes}/big-icons)

[Tiled icons](#/{notes}/tiled-icons) 

[Tiled icons](#/{notes}/tiled-icons)


**Format:** 


 icon\_states(Icon, mode=0)
 


**Format:** 

**Format:**

 icon\_states(Icon, mode=0)



**Returns:** 


 A list of text strings.
 


**Returns:** 

**Returns:**

 A list of text strings.



**Args:** 


 Icon: the icon being accessed
 
 mode: applies to icons larger than one tile when using map\_format=TILED\_ICON\_MAP; see below
 



**Args:** 

**Args:**

 Icon: the icon being accessed
 
 mode: applies to icons larger than one tile when using map\_format=TILED\_ICON\_MAP; see below
 


 mode: applies to icons larger than one tile when using map\_format=TILED\_ICON\_MAP; see below


 Icons may have one or more internal states, which are identified by name.
The state "" is the default.




 If you are not using the TILED\_ICON\_MAP value for world.map\_format, you
can ignore the mode argument.




 When graphics bigger than world.icon\_size are used as an icon, and the
map\_format in use is TILED\_ICON\_MAP, they are internally broken up into
tiles, one per icon state. The
 
 mode
 
 argument was added for big
icons that get split into several smaller tiles. Those icons have several
smaller states per true icon\_state. For example if your 64×64 icon
has a state named "open", it will contain states "open", "open 0,0",
"open 1,0", "open 0,1", and "open 1,1" which are all used internally.
(If the state name is blank, the sub-states are just "0,0", etc.) When using
the TILED\_ICON\_MAP format, you need these for displaying the icon over
several different atoms.




 mode


 mode=0 will only show the sub-states ("open 0,0" and so on), all of which
can be safely extracted in a single-tile icon via the
 
 icon()
 
 proc.
mode=1 will show the main state names ("open"); any time you work with that
state name you're working with the full-size icon. mode=2 will show all of
the states.




 icon()



---


