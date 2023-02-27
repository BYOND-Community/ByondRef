

 url\_encode proc
------------------




**See also:** 


[url\_decode proc](#/proc/url_decode) 



**See also:** 

**See also:**

[url\_decode proc](#/proc/url_decode) 

[url\_decode proc](#/proc/url_decode)


**Format:** 


 url\_encode(PlainText, format=0)
 


**Format:** 

**Format:**

 url\_encode(PlainText, format=0)



**Args:** 


 PlainText: text to be URL "escaped"
 
 format: 0 to treat PlainText as a query string, 1 to treat it as a full URL
 



**Args:** 

**Args:**

 PlainText: text to be URL "escaped"
 
 format: 0 to treat PlainText as a query string, 1 to treat it as a full URL
 


 format: 0 to treat PlainText as a query string, 1 to treat it as a full URL



**Returns:** 


 escaped text
 


**Returns:** 

**Returns:**

 escaped text


 Special characters such as spaces are not used literally in URLs.
If you want to ensure that an entire text string is sent literally, you can
"escape" those characters. For example, a double quote (ASCII 34) is produced
by the code
 `%22` 
 , where 22 is hexadecimal for 34.



`%22`

 The
 `url_encode()` 
 instruction does this for you
automatically. Using
 `format=1` 
 will treat the URL as already
encoded and only re-encode characters that don't belong in the result.
Otherwise PlainText is treated as part of a query string; in this case spaces
are converted to
 `+` 
 instead of
 `%20` 
 , and most
characters are escaped.



`url_encode()`
`format=1`
`+`
`%20`
### 
 Example:



 mob/verb/Private(M as mob in players, T as text)
 if(!client || !M || !M.client || !T) return
 usr << "\[To
 [[M.name]](?msg=[url_encode(M.key)]) 
 \] [T]"
 M << "\[From
 [[name]](?msg=[url_encode(key)]) 
 \] [T]"

[[M.name]](?msg=[url_encode(M.key)])
[[name]](?msg=[url_encode(key)])


---


