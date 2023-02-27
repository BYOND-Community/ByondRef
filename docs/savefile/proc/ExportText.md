

 ExportText proc (savefile)
----------------------------




**See also:** 


[ImportText proc (savefile)](#/savefile/proc/ImportText) 



**See also:** 

**See also:**

[ImportText proc (savefile)](#/savefile/proc/ImportText) 

[ImportText proc (savefile)](#/savefile/proc/ImportText)


**Format:** 


 savefile.ExportText(path=cd,file)
 


**Format:** 

**Format:**

 savefile.ExportText(path=cd,file)



**Args:** 


 path: the path to export
 
 file: optional file to write to
 



**Args:** 

**Args:**

 path: the path to export
 
 file: optional file to write to
 


 file: optional file to write to


 Converts all or part of a savefile to a human readable text format, similar
in syntax to DM. If no file is specified, the savefile text is returned as a
text string instead of being written to a file.




 The following example shows how to export and later import a savefile. The
user's mob is written into a directory with the same name as their
 [ckey](#/mob/var/ckey) 
 and the result is written to a text file.



[ckey](#/mob/var/ckey)
### 
 Example:



 mob/verb/write()
 var/savefile/F = new()
 var/txtfile = file("players/[ckey].txt")

 F[ckey] << usr

 fdel(txtfile)
 F.ExportText("/",txtfile)

 usr << "Your savefile looks like this:"
 usr << "
 
```
[html_encode(file2text(txtfile))]
```

 "

mob/verb/read()
 var/savefile/F = new()
 var/txtfile = file("players/[ckey].txt")

 F.ImportText("/",txtfile)
 F[ckey] >> usr


```
[html_encode(file2text(txtfile))]
```



---


