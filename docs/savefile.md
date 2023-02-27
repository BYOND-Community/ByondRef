

 savefile
----------




**See also:** 


[>> operator (savefile)](#/savefile/operator/%3e%3e) 

[<< operator (savefile)](#/savefile/operator/%3c%3c) 

[Export proc (client)](#/client/proc/Export) 

[New proc (client)](#/client/proc/New) 

[procs (savefile)](#/savefile/proc) 

[vars (savefile)](#/savefile/var) 

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 












**See also:** 

**See also:**

[>> operator (savefile)](#/savefile/operator/%3e%3e) 

[<< operator (savefile)](#/savefile/operator/%3c%3c) 

[Export proc (client)](#/client/proc/Export) 

[New proc (client)](#/client/proc/New) 

[procs (savefile)](#/savefile/proc) 

[vars (savefile)](#/savefile/var) 

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 










[>> operator (savefile)](#/savefile/operator/%3e%3e)

[<< operator (savefile)](#/savefile/operator/%3c%3c) 

[Export proc (client)](#/client/proc/Export) 

[New proc (client)](#/client/proc/New) 

[procs (savefile)](#/savefile/proc) 

[vars (savefile)](#/savefile/var) 

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 









[<< operator (savefile)](#/savefile/operator/%3c%3c)

[Export proc (client)](#/client/proc/Export) 

[New proc (client)](#/client/proc/New) 

[procs (savefile)](#/savefile/proc) 

[vars (savefile)](#/savefile/var) 

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 








[Export proc (client)](#/client/proc/Export)

[New proc (client)](#/client/proc/New) 

[procs (savefile)](#/savefile/proc) 

[vars (savefile)](#/savefile/var) 

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 







[New proc (client)](#/client/proc/New)

[procs (savefile)](#/savefile/proc) 

[vars (savefile)](#/savefile/var) 

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 






[procs (savefile)](#/savefile/proc)

[vars (savefile)](#/savefile/var) 

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 





[vars (savefile)](#/savefile/var)

[tmp vars](#/var/tmp) 

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 




[tmp vars](#/var/tmp)

[issaved proc](#/proc/issaved) 

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 



[issaved proc](#/proc/issaved)

[Read proc (datum)](#/datum/proc/Read) 

[Write proc (datum)](#/datum/proc/Write) 


[Read proc (datum)](#/datum/proc/Read)

[Write proc (datum)](#/datum/proc/Write) 

[Write proc (datum)](#/datum/proc/Write)


 Savefiles are easy to use, but you should always plan what you're going to
save and what you don't want to save. Use
 
 /tmp
 
 to avoid saving
anything you don't need, and you can avoid a lot of trouble.
 



 In particular you should be careful that if you're saving a player's mob,
you don't accidentally save any other mobs. If you save a turf, you should
avoid saving its contents unless you know there are no mobs standing on it
(but usually it's better to save x,y,z coordinates than the turf itself).
This is explained further in the
 [tmp vars](#/var/tmp) 
 entry.
 



 Currently, overlays and underlays also save by combining each list into a
single icon that saves its full icon data in the file. This may not be
desired, so you can remove that data. Usually you'll want to rebuild any
overlay/underlay lists during
 [Read()](#/datum/proc/Read) 
 .
 




 Savefiles are easy to use, but you should always plan what you're going to
save and what you don't want to save. Use
 
 /tmp
 
 to avoid saving
anything you don't need, and you can avoid a lot of trouble.




 /tmp


 In particular you should be careful that if you're saving a player's mob,
you don't accidentally save any other mobs. If you save a turf, you should
avoid saving its contents unless you know there are no mobs standing on it
(but usually it's better to save x,y,z coordinates than the turf itself).
This is explained further in the
 [tmp vars](#/var/tmp) 
 entry.



[tmp vars](#/var/tmp)

 Currently, overlays and underlays also save by combining each list into a
single icon that saves its full icon data in the file. This may not be
desired, so you can remove that data. Usually you'll want to rebuild any
overlay/underlay lists during
 [Read()](#/datum/proc/Read) 
 .



[Read()](#/datum/proc/Read)

 A database file in DM is called a "savefile". All of the contents of a
savefile reside in a single file. The contents of the file are stored in
database directories. These should not be confused with real directories in
the external file system. The database directories are all contained inside
the one file.




 Each database directory contains a list of sub-directories and a buffer in
which data may be written. The absolute path to a directory has the following
format: "/Dir1/Dir2/...". The current directory may be set by assigning its
absolute path name to
 `savefile.cd` 
 . A relative path (one that
doesn't begin with "/") may also be used, in which case the new path starts at
the current directory. The path "." stands for the current directory, ".."
for its parent, "../.." for its parent's parent, etc.



`savefile.cd`

 A savefile may be created with
 `new/savefile(name)` 
 . The
optional name argument may be an external file name (existing or to be
created) in double quotes or a file from the resource cache in single quotes.
Of course, a variable containing either of these types of values may also be
used. If no name is specified, a temporary file will be created, which will
be destroyed when the savefile is no longer in use. If a resource cache is
specified, a temporary file will be created and the contents of the cached
file will be copied into it. Changes will therefore only be temporary.



`new/savefile(name)`


---


