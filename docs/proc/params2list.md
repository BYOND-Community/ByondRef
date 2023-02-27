

 params2list proc
------------------




**See also:** 


[Topic proc (client)](#/client/proc/Topic) 

[list associations](#/list/associations) 

[list2params proc](#/proc/list2params) 

[params var (world)](#/world/var/params) 

[text2num proc](#/proc/text2num) 







**See also:** 

**See also:**

[Topic proc (client)](#/client/proc/Topic) 

[list associations](#/list/associations) 

[list2params proc](#/proc/list2params) 

[params var (world)](#/world/var/params) 

[text2num proc](#/proc/text2num) 





[Topic proc (client)](#/client/proc/Topic)

[list associations](#/list/associations) 

[list2params proc](#/proc/list2params) 

[params var (world)](#/world/var/params) 

[text2num proc](#/proc/text2num) 




[list associations](#/list/associations)

[list2params proc](#/proc/list2params) 

[params var (world)](#/world/var/params) 

[text2num proc](#/proc/text2num) 



[list2params proc](#/proc/list2params)

[params var (world)](#/world/var/params) 

[text2num proc](#/proc/text2num) 


[params var (world)](#/world/var/params)

[text2num proc](#/proc/text2num) 

[text2num proc](#/proc/text2num)


**Format:** 


 params2list(Params)
 


**Format:** 

**Format:**

 params2list(Params)



**Args:** 


 Params: Text string of parameter values.
 


**Args:** 

**Args:**

 Params: Text string of parameter values.



**Returns:** 


 An associative list of parameter names and values.
 


**Returns:** 

**Returns:**

 An associative list of parameter names and values.


 This instruction converts a parameter text string to a list of individual
parameters and associated values. The format of the parameter text is:




 "name1=value1&name2=value2&..."


 The field separator
 
 ;
 
 may be used in place of
 
 &
 
 .




 ;


 &


 Special characters such as
 
 =
 
 ,
 
 ;
 
 , and
 
 &
 
 inside the parameter names or values should be written in the form
 `%xx` 
 , where
 `xx` 
 are two hexadecimal digits
representing the ASCII value of the character. (For
 [Unicode](#/{notes}/Unicode) 
 characters, this may be several
 `%xx` 
 sequences using UTF-8 encoding.) For example,
 
 =
 
 would be written
 `%3d` 
 ,
 
 ;
 
 would be
 `%3b` 
 ,
 
 &
 
 would be
 `%26` 
 , and
 
 %
 
 would be
 `%25` 
 . These "escaped" codes are automatically translated
into the corresponding character when read by
 
 params2list()
 
 .




 =


 ;


 &

`%xx`
`xx`
[Unicode](#/{notes}/Unicode)
`%xx`

 =

`%3d`

 ;

`%3b`

 &

`%26`

 %

`%25`

 params2list()


 This parameter format is the same one used by most HTML forms and is
known by the MIME type
 
 application/x-www-form-urlencoded
 
 . It is
often used in DM to pack information into topic links. Though DM does not
require it, the standard format is for newlines to be written as CR LF pairs
(
 `%0d%0a` 
 ) and spaces to be written as
 
 +
 
 characters. That
means if you want to write a
 
 +
 
 symbol, you will have to use
 `%2b` 
 .




 application/x-www-form-urlencoded

`%0d%0a`

 +


 +

`%2b`

 The list produced from the parameter text has items
 
 "name1"
 
 ,
 
 "name2"
 
 , and so on. To access the values associated with these, you
use the parameter name as the list index.




 "name1"


 "name2"

### 
 Example:



 var/ptext = "offense=jwalk&time=10:00"
var/plist[] = params2list(ptext)

var/p
for(p in plist)
 usr << "[p] = [plist[p]]"


 The above example defines a simple parameter text string containing two
parameters:
 
 "offense"
 
 and
 
 "time"
 
 . These are associated with
the values
 
 "jwalk"
 
 and
 
 "10:00"
 
 . The
 `for` 
 loop
illustrates how one might loop through the list and print out each setting.




 "offense"


 "time"


 "jwalk"


 "10:00"

`for`

 Note that all values are stored as text strings in the list. If you wish
to perform a numerical operation (such as addition), you should convert the
value to a number first using
 
 text2num()
 
 . If the value is an object
text reference, you can convert that into the object itself by using
 
 locate()
 
 .




 text2num()


 locate()


 If you have multiple items with the same name, they will be combined into
a list of text strings. For example,
 
 "key=value1;key=value2"
 
 would
set
 
 list["key"]
 
 to a list containing
 
 "value1"
 
 and
 
 "value2"
 
 , not necessarily in that order.




 "key=value1;key=value2"


 list["key"]


 "value1"


 "value2"



---


