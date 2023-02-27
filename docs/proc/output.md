

 output proc
-------------




**See also:** 


[<< output operator](#/operator/%3c%3c/output) 

[winclone proc](#/proc/winclone) 

[winset proc](#/proc/winset) 





**See also:** 

**See also:**

[<< output operator](#/operator/%3c%3c/output) 

[winclone proc](#/proc/winclone) 

[winset proc](#/proc/winset) 



[<< output operator](#/operator/%3c%3c/output)

[winclone proc](#/proc/winclone) 

[winset proc](#/proc/winset) 


[winclone proc](#/proc/winclone)

[winset proc](#/proc/winset) 

[winset proc](#/proc/winset)


**Format:** 


 output(msg, control)
 


**Format:** 

**Format:**

 output(msg, control)



**Args:** 


 msg: Text, an atom, a file, or null
 
 control: The ID of a control in the player's skin, or null for the default
 



**Args:** 

**Args:**

 msg: Text, an atom, a file, or null
 
 control: The ID of a control in the player's skin, or null for the default
 


 control: The ID of a control in the player's skin, or null for the default


 This is used in conjunction with the << output operator to send
output to a particular control in the player's skin. If null is sent, the
control will be cleared.



### 
 Example:



 usr << output("Your score is [score].", "scorepane.output")


 As with
 
 winset()
 
 , the control name may be in the form
 
 ":[type]"
 
 which sends to the default control of that type, e.g.
 
 ":output"
 
 .




 winset()


 ":[type]"


 ":output"


 The control ID can be followed by a colon and extra info such as a name
or a grid cell, which can send the output to the control in a different way.
In a grid, this can output directly to a specific grid cell, like so:



### 
 Example:



 usr << output("Column 3, Row 2", "examplegrid:3,2")


 For a browser control, the extra info is a JavaScript function. The format
for sending a script to the browser control is
 
 output("[params]","[control]:[scriptname]")
 
 where "[params]" is a
URL-encoded list of string arguments to the javascript function, as formatted
by
 [list2params()](#/proc/list2params) 
 .




 output("[params]","[control]:[scriptname]")

[list2params()](#/proc/list2params)
### 
 Example:



 mob/Login()
 . = ..()
 usr << output(\
{"
 
 function replace(v) {
 document.getElementById('foo').innerHTML =
 v.replace(/&/g, '&amp;').replace(/</g, '&lt;');
}
 

 This text can change.
 

 And this can't.
 


 "},
 ":browser");

#define LP(str) list2params(list(str))
mob/verb/newtext(T as text)
 usr << output(LP(T), ":browser:replace")


 function replace(v) {
 document.getElementById('foo').innerHTML =
 v.replace(/&/g, '&amp;').replace(/</g, '&lt;');
}


 This text can change.


 And this can't.




 This allows for the creation of more dynamic interfaces, since javascript
provides access to many client-side operations and flicker-free updates.





---


