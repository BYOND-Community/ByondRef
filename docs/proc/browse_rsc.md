

 browse\_rsc proc
------------------




**See also:** 


[browse proc](#/proc/browse) 



**See also:** 

**See also:**

[browse proc](#/proc/browse) 

[browse proc](#/proc/browse)


**Format:** 


 usr << browse\_rsc(File,FileName)
 


**Format:** 

**Format:**

 usr << browse\_rsc(File,FileName)



**Args:** 


 File: a resource file (such as an image)
 
 FileName: name of file (if different from source file)
 



**Args:** 

**Args:**

 File: a resource file (such as an image)
 
 FileName: name of file (if different from source file)
 


 FileName: name of file (if different from source file)


 This sends the specified resource file to usr (or anybody else) and
stores it in their
 `cache` 
 directory with the specified name. In
subsequent
 `browse()` 
 output, you can then refer to that file.



`cache`
`browse()`

 If your world is always running on the internet, you can save yourself
the trouble and simply link to the image files through a web server.
However, if it may be played offline, you can compile in the resource files
and manually send them to players with
 `browse_rsc()` 
 .



`browse_rsc()`

 Note that no data is transmitted if it already exists in the user's
cache, so there is little overhead in calling this every time you are about
to use
 `browse()` 
 .



`browse()`
### 
 Example:



 area
 var
 room\_graphic = 'cozy\_room.jpg'
 Enter(O)
 . = ..() //do default checks
 if(.) //if we got clearance to enter
 O << browse\_rsc(room\_graphic,"room.jpg")
 O << browse("
 
![](room.jpg)



 [desc]")


![](room.jpg)



![](room.jpg)


---


