

 json\_decode proc
-------------------




**See also:** 


[json\_encode proc](#/proc/json_encode) 



**See also:** 

**See also:**

[json\_encode proc](#/proc/json_encode) 

[json\_encode proc](#/proc/json_encode)


**Format:** 


 json\_decode(JSON)
 
 json\_decode(JSON, flags)
 



**Format:** 

**Format:**

 json\_decode(JSON)
 
 json\_decode(JSON, flags)
 


 json\_decode(JSON, flags)



**Returns:** 


 A value interpreted from a JSON-formatted text string.
 


**Returns:** 

**Returns:**

 A value interpreted from a JSON-formatted text string.



**Args:** 


 JSON: The JSON-formatted text to decode.
 
 flags: A set of flags that tell the decoder how to act.
 



**Args:** 

**Args:**

 JSON: The JSON-formatted text to decode.
 
 flags: A set of flags that tell the decoder how to act.
 


 flags: A set of flags that tell the decoder how to act.


 Arrays like
 
 [1,2,3]
 
 will be converted to regular lists like
 
 list(1,2,3)
 
 .




 [1,2,3]


 list(1,2,3)


 Object literals like
 
 {"a":1}
 
 will be converted to associative
lists such as
 
 list("a"=1)
 
 . Each item in the list is also decoded.
Except in strict mode, non-string values are allowed as the "keys" in an
associaitve list, even though that's not valid JSON, and strings used as keys
can be left unquoted. BYOND doesn't care, as long as it can understand the
formatted text it's given. The only exception is that a number isn't allowed
to be an associative list key, and will be converted to a string instead, so
 
 {1:2}
 
 becomes
 
 list("1"=2)
 
 .




 {"a":1}


 list("a"=1)


 {1:2}


 list("1"=2)


 Special numbers
 
 NaN
 
 and
 
 Infinity
 
 are recognized correctly
(these are case-sensitive). All other numbers are parsed and stored in the
regular BYOND format (32-bit floating point).




 NaN


 Infinity


 Since BYOND doesn't have dedicated boolean values,
 
 true
 
 and
 
 false
 
 are interpreted as 1 and 0, respectively.




 true


 false


 The
 
 JSON\_STRICT
 
 flag uses stricter JSON parsing rules and will
not allow some things. In strict mode:




 JSON\_STRICT

* All strings must be double-quoted.
* Special numbers
 
 NaN
 
 and
 
 Infinity
 
 are not allowed, but
 the
 
 {\_\_number\_\_:"NaN"}
 
 format used by
 
 json\_encode()
 
 is
 recognized as a number.
* Keys in an associative list must always be strings, and must be
 double-quoted.


- All strings must be double-quoted.

- Special numbers
 
 NaN
 
 and
 
 Infinity
 
 are not allowed, but
 the
 
 {\_\_number\_\_:"NaN"}
 
 format used by
 
 json\_encode()
 
 is
 recognized as a number.


 NaN


 Infinity


 {\_\_number\_\_:"NaN"}


 json\_encode()

- Keys in an associative list must always be strings, and must be
 double-quoted.


 The
 
 JSON\_ALLOW\_COMMENTS
 
 flag allows you to include
 
 //
 
 single-line comments and
 
 /\* ... \*/
 
 long-form comments in the text to
be decoded. This can be mixed with the strict flag. This flag is now used by
default.




 JSON\_ALLOW\_COMMENTS


 //


 /\* ... \*/



---


