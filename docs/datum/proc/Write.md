

 Write proc (datum)
--------------------




**See also:** 


[<< operator (savefile)](#/savefile/operator/%3c%3c) 

[Read proc (datum)](#/datum/proc/Read) 

[initial proc](#/proc/initial) 

[issaved proc](#/proc/issaved) 

[tmp vars](#/var/tmp) 







**See also:** 

**See also:**

[<< operator (savefile)](#/savefile/operator/%3c%3c) 

[Read proc (datum)](#/datum/proc/Read) 

[initial proc](#/proc/initial) 

[issaved proc](#/proc/issaved) 

[tmp vars](#/var/tmp) 





[<< operator (savefile)](#/savefile/operator/%3c%3c)

[Read proc (datum)](#/datum/proc/Read) 

[initial proc](#/proc/initial) 

[issaved proc](#/proc/issaved) 

[tmp vars](#/var/tmp) 




[Read proc (datum)](#/datum/proc/Read)

[initial proc](#/proc/initial) 

[issaved proc](#/proc/issaved) 

[tmp vars](#/var/tmp) 



[initial proc](#/proc/initial)

[issaved proc](#/proc/issaved) 

[tmp vars](#/var/tmp) 


[issaved proc](#/proc/issaved)

[tmp vars](#/var/tmp) 

[tmp vars](#/var/tmp)


**Format:** 


 Write(savefile/F)
 


**Format:** 

**Format:**

 Write(savefile/F)



**When:** 


 Called when the object is written to a save file.
 


**When:** 

**When:**

 Called when the object is written to a save file.



**Args:** 


 F: the save file being written to
 


**Args:** 

**Args:**

 F: the save file being written to



**Default action:** 


 Write the value of each variable to a directory by the same name as the
 variable. Variables marked tmp, global, or const and variables which
 are equal to their initial value are skipped.
 


**Default action:** 

**Default action:**

 Write the value of each variable to a directory by the same name as the
 variable. Variables marked tmp, global, or const and variables which
 are equal to their initial value are skipped.



---


