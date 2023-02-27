

 FILE\_DIR definition
----------------------




**See also:** 


[cache](#/DM/cache) 

[icons](#/DM/icon) 




**See also:** 

**See also:**

[cache](#/DM/cache) 

[icons](#/DM/icon) 


[cache](#/DM/cache)

[icons](#/DM/icon) 

[icons](#/DM/icon)


**Format:** 


 #define FILE\_DIR Path
 


**Format:** 

**Format:**

 #define FILE\_DIR Path



**Args:** 


 Path: A search path on the current filesystem.
 


**Args:** 

**Args:**

 Path: A search path on the current filesystem.


 This macro defines a search path to be used in evaluating resource files
(icons and sounds). First the current directory is searched, then the first
 `FILE_DIR` 
 path, then the next, etc.



`FILE_DIR`
### 
 Example:



 #define FILE\_DIR icons
#define FILE\_DIR icons/mobs

mob/clown
 icon = 'clown.dmi'


 This searches for the file at the paths
 `"./clown.dmi"` 
 ,
 `"./icons/clown.dmi"` 
 , and
 `"./icons/sounds/clown.dmi"` 
 ,
where
 `"."` 
 is the directory of the current source file.



`"./clown.dmi"`
`"./icons/clown.dmi"`
`"./icons/sounds/clown.dmi"`
`"."`


---


