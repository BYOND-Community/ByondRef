

 run proc
----------




**See also:** 


[<< output operator](#/operator/%3c%3c/output) 

[file proc](#/proc/file) 

[link proc](#/proc/link) 





**See also:** 

**See also:**

[<< output operator](#/operator/%3c%3c/output) 

[file proc](#/proc/file) 

[link proc](#/proc/link) 



[<< output operator](#/operator/%3c%3c/output)

[file proc](#/proc/file) 

[link proc](#/proc/link) 


[file proc](#/proc/file)

[link proc](#/proc/link) 

[link proc](#/proc/link)


**Format:** 


 O << run(File)
 


**Format:** 

**Format:**

 O << run(File)


 This is similar to link() but instead of a URL, you can pass a file to be
viewed directly. The file may be a cache file or an external file.



### 
 Example:



 mob/var/picture = 'mob.jpg'
mob/verb/view\_pic(mob/M as mob in view())
 usr << run(M.picture)

mob/verb/set\_pic(F as file)
 usr.picture = F


 This example defines a picture to be associated with each mob and a verb
for viewing another mob's picture. Players can also configure their own
pictures.





---


