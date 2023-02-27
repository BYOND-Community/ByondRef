

 << output operator
--------------------




**See also:** 


[<< operator (savefile)](#/savefile/operator/%3c%3c) 

[output proc](#/proc/output) 

[browse proc](#/proc/browse) 

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[ftp proc](#/proc/ftp) 

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 













**See also:** 

**See also:**

[<< operator (savefile)](#/savefile/operator/%3c%3c) 

[output proc](#/proc/output) 

[browse proc](#/proc/browse) 

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[ftp proc](#/proc/ftp) 

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 











[<< operator (savefile)](#/savefile/operator/%3c%3c)

[output proc](#/proc/output) 

[browse proc](#/proc/browse) 

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[ftp proc](#/proc/ftp) 

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 










[output proc](#/proc/output)

[browse proc](#/proc/browse) 

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[ftp proc](#/proc/ftp) 

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 









[browse proc](#/proc/browse)

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[ftp proc](#/proc/ftp) 

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 








[browse\_rsc proc](#/proc/browse_rsc)

[file proc](#/proc/file) 

[ftp proc](#/proc/ftp) 

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 







[file proc](#/proc/file)

[ftp proc](#/proc/ftp) 

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 






[ftp proc](#/proc/ftp)

[image proc](#/proc/image) 

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 





[image proc](#/proc/image)

[link proc](#/proc/link) 

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 




[link proc](#/proc/link)

[load\_resource proc](#/proc/load_resource) 

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 



[load\_resource proc](#/proc/load_resource)

[run proc](#/proc/run) 

[sound proc](#/proc/sound) 


[run proc](#/proc/run)

[sound proc](#/proc/sound) 

[sound proc](#/proc/sound)


**Format:** 


 A << B
 


**Format:** 

**Format:**

 A << B


 Cause the value B to be output to any players connected to mobs specified
in A.




 B may be an image, sound, or text. A may be a mob, the whole world, or
any list containing mobs.



### 
 Example:



 usr << "Hi, [usr.name]"
view() << "To all in view"
world << "Hi everybody!"

usr << 'giggle.wav'
view() << image(/obj/Fireball,usr)



---


