

 cache
-------




**See also:** 


[FILE\_DIR definition](#/DM/preprocessor/define/FILE_DIR) 

[cache\_lifespan var (world)](#/world/var/cache_lifespan) 

[fcopy\_rsc proc](#/proc/fcopy_rsc) 

[file proc](#/proc/file) 

[icons](#/DM/icon) 

[sounds](#/DM/sound) 








**See also:** 

**See also:**

[FILE\_DIR definition](#/DM/preprocessor/define/FILE_DIR) 

[cache\_lifespan var (world)](#/world/var/cache_lifespan) 

[fcopy\_rsc proc](#/proc/fcopy_rsc) 

[file proc](#/proc/file) 

[icons](#/DM/icon) 

[sounds](#/DM/sound) 






[FILE\_DIR definition](#/DM/preprocessor/define/FILE_DIR)

[cache\_lifespan var (world)](#/world/var/cache_lifespan) 

[fcopy\_rsc proc](#/proc/fcopy_rsc) 

[file proc](#/proc/file) 

[icons](#/DM/icon) 

[sounds](#/DM/sound) 





[cache\_lifespan var (world)](#/world/var/cache_lifespan)

[fcopy\_rsc proc](#/proc/fcopy_rsc) 

[file proc](#/proc/file) 

[icons](#/DM/icon) 

[sounds](#/DM/sound) 




[fcopy\_rsc proc](#/proc/fcopy_rsc)

[file proc](#/proc/file) 

[icons](#/DM/icon) 

[sounds](#/DM/sound) 



[file proc](#/proc/file)

[icons](#/DM/icon) 

[sounds](#/DM/sound) 


[icons](#/DM/icon)

[sounds](#/DM/sound) 

[sounds](#/DM/sound)

 Files specified in single quotes are loaded (at compile time) into the
world cache file (ending in
 `.rsc` 
 ). These are referred to as
resource files. At runtime these files are downloaded by players into their
 `byond.rsc` 
 file for future use. With the appropriate verbs or
through savefiles, players may also upload files into the world cache.



`.rsc`
`byond.rsc`

 If a resource file is not used for a long time, it will be automatically
removed from the cache file to save space. If a cache file gets too bulky,
however, you may manually delete it and start from scratch.




 To make compilation faster and to make it easier to distribute code, the
compiler will use an existing cache file if possible. That means you could
compile up a world, and send people the
 `.dm` 
 and
 `.rsc` 
 files without any need to package all the individual
resource files. It is also possible to include additional supplementary
 `.rsc` 
 files by using the
 `#include` 
 statement.



`.dm`
`.rsc`
`.rsc`
`#include`


---


