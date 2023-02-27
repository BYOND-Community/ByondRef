

 json\_encode proc
-------------------




**See also:** 


[json\_decode proc](#/proc/json_decode) 



**See also:** 

**See also:**

[json\_decode proc](#/proc/json_decode) 

[json\_decode proc](#/proc/json_decode)


**Format:** 


 json\_encode(Value)
 
 json\_encode(Value, flags)
 



**Format:** 

**Format:**

 json\_encode(Value)
 
 json\_encode(Value, flags)
 


 json\_encode(Value, flags)



**Returns:** 


 A JSON-formatted text string representing Value.
 


**Returns:** 

**Returns:**

 A JSON-formatted text string representing Value.



**Args:** 


 Value: The value to encode.
 
 flags: A set of flags that tell the encoder how to act.
 



**Args:** 

**Args:**

 Value: The value to encode.
 
 flags: A set of flags that tell the encoder how to act.
 


 flags: A set of flags that tell the encoder how to act.


 If Value is a simple list or a matrix, the result will be formatted as a
JSON array, and each item in the list is encoded.




 If Value is an associative list, the result will be formatted as a JSON
object literal, and each item and associated value is encoded. (The keys in
the object literal don't have to be strings. Even though that isn't valid
JSON, BYOND doesn't care. Be aware however that strict JSON parsers
 *will* 
 care.)



*will*

 Datums are
 *not* 
 serialized, but are converted to the equivalent of
 
 "[Value]"
 
 instead.



*not*

 "[Value]"


 The special numbers NaN and infinity will be encoded as object literals
in a form like
 
 {"\_\_number\_\_":"NaN"}
 
 .




 {"\_\_number\_\_":"NaN"}

### 
 Example:



 var/list/info = list("name"="fridge", "power"=12)
// send {"name":"fridge","power":12} to a JavaScript function
usr << output(url\_encode(json\_encode(info)), "mybrowser:myJSfunction")


 BYOND formatting such as \red is removed from encoded strings.




 Situations where a list has a reference to itself will cause the nested
version to print a null value instead.




 The
 
 JSON\_PRETTY\_PRINT
 
 flag introduces spacing into the output for
improved readibility. Spaces will be added after colons and commas. Non-empty
arrays and object literals will have a line break and tabs before each item,
and a line break with one fewer tab before the closing bracket or brace. (The
special formatting for numbers like Infinity, or the list form for matrices,
will not be given tabs and line breaks.)




 JSON\_PRETTY\_PRINT



---


