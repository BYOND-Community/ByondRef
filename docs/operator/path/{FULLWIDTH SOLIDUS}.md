

 / path operator
-----------------




**See also:** 


[. path operator](#/operator/path/%2e) 

[: path operator](#/operator/path/:) 




**See also:** 

**See also:**

[. path operator](#/operator/path/%2e) 

[: path operator](#/operator/path/:) 


[. path operator](#/operator/path/%2e)

[: path operator](#/operator/path/:) 

[: path operator](#/operator/path/:)

 This is used to delimit paths in the DM code tree. A path beginning with
'/' is an absolute path (which is independent of where in the code it is
used). Otherwise, a path is relative, meaning it starts from the current
position in the code.




 The following example uses a path in the code tree to define the type of
object to create when leaving a corpse behind.



### 
 Example:



 obj
 var
 poison
 nutrition

 corpse
 frog
 nutrition = 10
 spider
 nutrition = 6
 poison = 5
mob
 var
 corpse = /obj/corpse
 Die()
 new corpse(src.loc) //create the corpse here
 del src

 spider
 corpse = /obj/corpse/spider
 frog
 corpse = /obj/corpse/frog



---


