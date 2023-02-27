

 html\_decode proc
-------------------




**See also:** 


[html\_encode proc](#/proc/html_encode) 



**See also:** 

**See also:**

[html\_encode proc](#/proc/html_encode) 

[html\_encode proc](#/proc/html_encode)


**Format:** 


 html\_decode(HtmlText)
 


**Format:** 

**Format:**

 html\_decode(HtmlText)



**Args:** 


 HtmlText: text to be "unescaped"
 


**Args:** 

**Args:**

 HtmlText: text to be "unescaped"



**Returns:** 


 unescaped text
 


**Returns:** 

**Returns:**

 unescaped text


 Special characters such as < and > are not displayed literally in
html and may produce garbled output. To display these characters literally,
they must be "escaped". For example, < is produced by the code
 `&lt;` 
 and > is produced by the code
 `&gt;` 
 .



`&lt;`
`&gt;`

 The
 `html_decode()` 
 instruction takes a text string containing
such escaped symbols and turns them into their literal counterparts. The
more useful function is
 `html_encode()` 
 which does the reverse.



`html_decode()`
`html_encode()`


---


