

 url\_decode proc
------------------




**See also:** 


[Topic proc (client)](#/client/proc/Topic) 

[url\_encode proc](#/proc/url_encode) 




**See also:** 

**See also:**

[Topic proc (client)](#/client/proc/Topic) 

[url\_encode proc](#/proc/url_encode) 


[Topic proc (client)](#/client/proc/Topic)

[url\_encode proc](#/proc/url_encode) 

[url\_encode proc](#/proc/url_encode)


**Format:** 


 url\_decode(UrlText)
 


**Format:** 

**Format:**

 url\_decode(UrlText)



**Args:** 


 UrlText: text to be "unescaped"
 


**Args:** 

**Args:**

 UrlText: text to be "unescaped"



**Returns:** 


 unescaped text
 


**Returns:** 

**Returns:**

 unescaped text


 Most non-alphanumeric characters are converted to another format in a URL.
To send these characters literally, they must be "escaped".




 The
 `url_decode()` 
 instruction takes a text string containing
such escaped symbols and turns them into their literal counterparts. Usually
this is done for you automatically in
 `Topic()` 
 . The more useful
function is
 `url_encode()` 
 which does the reverse.



`url_decode()`
`Topic()`
`url_encode()`


---


