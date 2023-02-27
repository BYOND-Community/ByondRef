

 New proc (savefile)
---------------------




**See also:** 


[Lock proc (savefile)](#/savefile/proc/Lock) 

[Unlock proc (savefile)](#/savefile/proc/Unlock) 




**See also:** 

**See also:**

[Lock proc (savefile)](#/savefile/proc/Lock) 

[Unlock proc (savefile)](#/savefile/proc/Unlock) 


[Lock proc (savefile)](#/savefile/proc/Lock)

[Unlock proc (savefile)](#/savefile/proc/Unlock) 

[Unlock proc (savefile)](#/savefile/proc/Unlock)


**Format:** 


 New(filename,timeout)
 


**Format:** 

**Format:**

 New(filename,timeout)



**Args:** 


 filename: name of file or empty for temporary file
 
 timeout: seconds to wait; -1 for no timeout
 



**Args:** 

**Args:**

 filename: name of file or empty for temporary file
 
 timeout: seconds to wait; -1 for no timeout
 


 timeout: seconds to wait; -1 for no timeout


 You call this via new/savefile(filename,timeout). The timeout is used to
determine how long to wait if the file is locked. Normally (timeout=0), if
the file is locked, the proc crashes with a runtime error. If you specify a
timeout, then it will keep trying to open the file and if this fails, it will
simply return with savefile.name being empty (ie a false value).




 If the first argument is an entry in the world's rsc cache, the data will
be copied into a temporary file and accessed from there. Changes to this, and
any other temporary file, are not saved. When you close the file, it simply
gets deleted.





---


