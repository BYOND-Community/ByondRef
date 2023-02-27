

 md5 proc
----------




**See also:** 


[sha1 proc](#/proc/sha1) 

[file proc](#/proc/file) 




**See also:** 

**See also:**

[sha1 proc](#/proc/sha1) 

[file proc](#/proc/file) 


[sha1 proc](#/proc/sha1)

[file proc](#/proc/file) 

[file proc](#/proc/file)


**Format:** 


 md5(T)
 
 md5(F)
 



**Format:** 

**Format:**

 md5(T)
 
 md5(F)
 


 md5(F)



**Returns:** 


 text or null.
 


**Returns:** 

**Returns:**

 text or null.



**Args:** 


 T: A text string.
 
 F: A file.
 



**Args:** 

**Args:**

 T: A text string.
 
 F: A file.
 


 F: A file.


 This proc implements MD5 hashing. A hash function is a one-way process
that compacts information to a short value: a hash. The same value will
always have the same hash. Among other uses, most computers use hashing
to store passwords. By storing just the hash, the password file contains
very little sensitive information, but the password can still be verified
by confirming that
 `md5(password)==hash` 
 . MD5 is a widely-used
hash function.



`md5(password)==hash`
### 
 Example:



 mob/var/hash

mob/Read(savefile/S)
 ..()
 // hash was saved in the file along with other values
 if(md5("[level]/[exp]/[exp\_needed]") != hash)
 src << "Cheater!"
 del(src)


 In the example, a few vars belonging to a mob were saved along with a hash
of those values. When the mob is loaded again, the game compares the hash
to the values to make sure it's still accurate. If the values or hash had
been changed by a sneaky player, they wouldn't match. (But a sneaky player
could still calculate
 `hash` 
 themselves if they knew the exact
text used to make it, so this should be kept secret.)



`hash`

 If the argument is a file,
 
 md5()
 
 will read the file and return the
MD5 hash of the file's entire contents. If the file doesn't exist, it returns
null. The file may be a cache file or an external file.




 md5()

### 
 Examples:



 var/hash = "(insert hash value here)" // Compute this ahead of time

// Check that the cached default icon is still the same
if (md5('default.dmi') != hash)
 world << "The default icon has been modified!"

// Or check that the entire game resource file is pristine
if (md5(file("mygame.rsc")) != hash)
 world << "The game resources have been modified!"


 Note that you must pass the result of
 [file()](#/proc/file) 
 in order to compute the hash of an external file's contents at runtime.
Otherwise
 
 md5()
 
 will treat the filename as text and return the hash
of the name only.



[file()](#/proc/file)

 md5()


 If
 
 T
 
 is anything but a text string or file, the proc returns null.




 T



---


