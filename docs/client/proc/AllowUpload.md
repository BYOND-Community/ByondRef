

 AllowUpload proc (client)
---------------------------




**See also:** 


[input proc](#/proc/input) 



**See also:** 

**See also:**

[input proc](#/proc/input) 

[input proc](#/proc/input)


**Format:** 


 AllowUpload(filename, filelength)
 


**Format:** 

**Format:**

 AllowUpload(filename, filelength)



**When:** 


 Called when the player attempts to upload a file to the server, through input() or a command.
 


**When:** 

**When:**

 Called when the player attempts to upload a file to the server, through input() or a command.



**Default action:** 


 Allows the upload by returning 1.
 


**Default action:** 

**Default action:**

 Allows the upload by returning 1.


 The client who owns this proc (src) is the one trying to upload the file.
If this proc returns a true value, the upload will be allowed. Otherwise, it
will be rejected.



### 
 Example:



 client
 AllowUpload(filename, filelength)
 if(filelength >= 524288) // 512K (0.5M)
 src << "[filename] is too big to upload!"
 return 0
 return 1



---


