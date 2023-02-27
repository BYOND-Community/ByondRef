

 browse proc
-------------




**See also:** 


[<< output operator](#/operator/%3c%3c/output) 

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[link proc](#/proc/link) 

[run proc](#/proc/run) 

[output proc](#/proc/output) 








**See also:** 

**See also:**

[<< output operator](#/operator/%3c%3c/output) 

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[link proc](#/proc/link) 

[run proc](#/proc/run) 

[output proc](#/proc/output) 






[<< output operator](#/operator/%3c%3c/output)

[browse\_rsc proc](#/proc/browse_rsc) 

[file proc](#/proc/file) 

[link proc](#/proc/link) 

[run proc](#/proc/run) 

[output proc](#/proc/output) 





[browse\_rsc proc](#/proc/browse_rsc)

[file proc](#/proc/file) 

[link proc](#/proc/link) 

[run proc](#/proc/run) 

[output proc](#/proc/output) 




[file proc](#/proc/file)

[link proc](#/proc/link) 

[run proc](#/proc/run) 

[output proc](#/proc/output) 



[link proc](#/proc/link)

[run proc](#/proc/run) 

[output proc](#/proc/output) 


[run proc](#/proc/run)

[output proc](#/proc/output) 

[output proc](#/proc/output)


**Format:** 


 usr << browse(Body,Options)
 


**Format:** 

**Format:**

 usr << browse(Body,Options)



**Args:** 


 Body: html text, file, or null to close the browser.
 
 Options: optional parameters
 



**Args:** 

**Args:**

 Body: html text, file, or null to close the browser.
 
 Options: optional parameters
 


 Options: optional parameters


 This sends the html text or file to the user and optionally displays it in
the web browser. The default action is to use the embedded browser panel in the Dream
Seeker window; specifying an alternate window name (see below) causes it to appear in a
popup window. Passing in 'null' for the html text causes the browser panel or named
window to be closed.




 The option parameters should either be omitted or they should be in a text
string of the following format:
 `"
 
 window
 
 =name;
 
 file
 
 =name;
 
 display
 
 =1;
   


 size
 
 =300x300;
 
 border
 
 =0;
 
 can\_close
 
 =1;
   


 can\_resize
 
 =1;
 
 can\_minimize
 
 =1;
 
 titlebar
 
 =1"` 



`"
 
 window
 
 =name;
 
 file
 
 =name;
 
 display
 
 =1;
   


 size
 
 =300x300;
 
 border
 
 =0;
 
 can\_close
 
 =1;
   


 can\_resize
 
 =1;
 
 can\_minimize
 
 =1;
 
 titlebar
 
 =1"`

 window


 file


 display

  


 size


 border


 can\_close

  


 can\_resize


 can\_minimize


 titlebar


 You may use commas (,), ampersands (&), or semicolons (;) as the
delimiter. Any or all of the parameters may be specified and they may be
included in any order.



### 
 General options








 window
 

 This is the name used to identify the popup window. It is not visible to
the user. Multiple calls to browse() with the same window name overwrite
previous contents of the same popup window. If window is not specified, the
embedded browser panel will be used.
 

 file
 

 When this is unspecified, the client will store the generated html file in the
user's byond "cache" directory with an appropriate name. If Body is a
text string, the client will generate a unique name. If it is a file, it will use
the name of the file. You can override this by setting this parameter. This is
only useful when you need to reference the file later, typically in tandem with the
display setting below.
 

 display
 

 This controls whether the browser actually displays Body in the web browser
or not. If it is turned off (display=0), the text or file is simply sent
to the user and expected to be referenced later. This might be useful, for instance, to first send an image to a user and then display a web page that uses that image:
 
 usr << browse('monster.png',"display=0")
usr << browse("
 ![](monster.png)
 A scary monster appears from the mist!")
 
 Note that this performs the same function as the
 [browse\_rsc](#/proc/browse_rsc) 
 proc (preserved for legacy reasons). It is a little more powerful because you can use
it to send html text as well as files. In that case, you'll have to also supply the file=name argument so that you can reference the html text from within a later browse().
 
 When display=0, all of the other arguments besides file are ignored.
 





 window


 This is the name used to identify the popup window. It is not visible to
the user. Multiple calls to browse() with the same window name overwrite
previous contents of the same popup window. If window is not specified, the
embedded browser panel will be used.


 file


 When this is unspecified, the client will store the generated html file in the
user's byond "cache" directory with an appropriate name. If Body is a
text string, the client will generate a unique name. If it is a file, it will use
the name of the file. You can override this by setting this parameter. This is
only useful when you need to reference the file later, typically in tandem with the
display setting below.


 display


 This controls whether the browser actually displays Body in the web browser
or not. If it is turned off (display=0), the text or file is simply sent
to the user and expected to be referenced later. This might be useful, for instance, to first send an image to a user and then display a web page that uses that image:
 
 usr << browse('monster.png',"display=0")
usr << browse("
 ![](monster.png)
 A scary monster appears from the mist!")
 
 Note that this performs the same function as the
 [browse\_rsc](#/proc/browse_rsc) 
 proc (preserved for legacy reasons). It is a little more powerful because you can use
it to send html text as well as files. In that case, you'll have to also supply the file=name argument so that you can reference the html text from within a later browse().
 
 When display=0, all of the other arguments besides file are ignored.
 




 usr << browse('monster.png',"display=0")
usr << browse("
 ![](monster.png)
 A scary monster appears from the mist!")

![](monster.png)
[browse\_rsc](#/proc/browse_rsc)

 When display=0, all of the other arguments besides file are ignored.



### 
 Popup options








 border
 

 This is the width of the border between the edges of the dialogue and the window
content. The default value is 0, meaning that the entire window is filled with
html content.
 

 size
 

 This is the size of the popup window in pixels. The format is
 `WIDTHxHEIGHT` 
 .
 

 can\_close
 

 This specifies whether the window should be closable. The default value
is 1, which enables the standard "X" button for closing.
 

 can\_resize
 

 This controls whether the window is resizable. The default value is 1,
enabling resizing and maximizing.
 

 can\_minimize
 

 This controls whether the window is minimizable. The default value is 1,
enabling the standard minimization button.
 

 titlebar
 

 The default titlebar=1 enables the standard bar at the top of the window.
Turning it off disables can\_close and can\_minimize.
 


 border


 This is the width of the border between the edges of the dialogue and the window
content. The default value is 0, meaning that the entire window is filled with
html content.


 size


 This is the size of the popup window in pixels. The format is
 `WIDTHxHEIGHT` 
 .

`WIDTHxHEIGHT`

 can\_close


 This specifies whether the window should be closable. The default value
is 1, which enables the standard "X" button for closing.


 can\_resize


 This controls whether the window is resizable. The default value is 1,
enabling resizing and maximizing.


 can\_minimize


 This controls whether the window is minimizable. The default value is 1,
enabling the standard minimization button.


 titlebar


 The default titlebar=1 enables the standard bar at the top of the window.
Turning it off disables can\_close and can\_minimize.


 Note also that many display options can be controlled through the html
itself. For instance, to turn off the scrollbars, you can do:
 `<body scroll=no>` 
 ; to add a title, you can do:
 `<head><title>My Title</title></head>` 
 ; and so forth.



`<body scroll=no>`
`<head><title>My Title</title></head>`

 The following example displays a help page in a popup window.



### 
 Example:



 var/const/help = {"
 
 Help!
 
 You are beyond help!



"}
client/verb/help()
 usr << browse(help,"window=help")


 Help!

[output()](#/proc/output)
[winset()](#/proc/winset)
### 
 Example:



 client/verb/more\_help()
 usr << output("You are still beyond help!", "help.browser")



---


