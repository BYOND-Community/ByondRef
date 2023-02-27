

 browser control (skin)
------------------------



 A browser panel integrated into the skin.





**Browser-specific parameters:** 


[auto-format](#/{skin}/param/auto-format) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[show-history](#/{skin}/param/show-history) 

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 








**Browser-specific parameters:** 

**Browser-specific parameters:**

[auto-format](#/{skin}/param/auto-format) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[show-history](#/{skin}/param/show-history) 

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 






[auto-format](#/{skin}/param/auto-format)

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[show-history](#/{skin}/param/show-history) 

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 





[on-hide](#/{skin}/param/on-hide)

[on-show](#/{skin}/param/on-show) 

[show-history](#/{skin}/param/show-history) 

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 




[on-show](#/{skin}/param/on-show)

[show-history](#/{skin}/param/show-history) 

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 



[show-history](#/{skin}/param/show-history)

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 


[show-url](#/{skin}/param/show-url)

[use-title](#/{skin}/param/use-title) 

[use-title](#/{skin}/param/use-title)

 Browsers are capable of displaying HTML documents, and can also interact with the skin.



### 
 Browsers and popups



 A longstanding behavior of BYOND is the ability to create a new browser window by sending an extra argument to the
 [browse()](#/proc/browse) 
 proc. Since the advent of skins in BYOND 4.0, this behavior was kept. When you create a new browser popup, the window name you specify for the popup is used for the name of a new
 [window control](#/{skin}/control/main) 
 , and within that window there will be a new browser control simply called
 
 browser
 
 .



[browse()](#/proc/browse)
[window control](#/{skin}/control/main)

 browser


 If you want to interact with the new browser, its full "decorated"
 [id](#/{skin}/param/id) 
 is
 
*windowname* 
 .browser
 
 .



[id](#/{skin}/param/id)

*windowname* 
 .browser

*windowname*
### 
 Running JavaScript from DM



 Sending
 [output()](#/proc/output) 
 to a browser will send a document to display there, but if you follow the browser's control name with a colon and a function name, you can call a JavaScript function in the document displayed within that browser.



[output()](#/proc/output)
### 
 Example:



 var/list/info = list("name"="fridge", "power"=12)
// send {"name":"fridge","power":12} to a JavaScript function
usr << output(url\_encode(json\_encode(info)), "mybrowser:myJSfunction")


 The text that you send as output will be parsed like URL parameters, where mutliple arguments to the function are separated by
 
 &
 
 or
 
 ;
 
 , which is why
 [url\_encode()](#/proc/url_encode) 
 is wrapped around the
 [json\_encode()](#/proc/json_encode) 
 call in this example.




 &


 ;

[url\_encode()](#/proc/url_encode)
[json\_encode()](#/proc/json_encode)
### 
 Winset and Winget via JavaScript



 To allow better access to the skin via JavaScript, two new URL formats have been added. If
 
 window.location
 
 is set to these from JavaScript in a browser control, they can be used to interact directly.




 window.location


**Winset URL:** 

 byond://winset?id=
 *[control ID]* 
 &
 *[property]* 
 =
 *[value]* 
 &...
 



**Winset URL:**

 byond://winset?id=
 *[control ID]* 
 &
 *[property]* 
 =
 *[value]* 
 &...

*[control ID]*
*[property]*
*[value]*

 This works like an ordinary
 [winset()](#/proc/winset) 
 call from the server. If
 
 id
 
 is omitted, it's the same as a winset with a null ID. You can also leave the
 
 id
 
 blank if you use "fully decorated" property names such as
 
 mybutton.is-checked
 
 instead of just
 
 is-checked
 
 .



[winset()](#/proc/winset)

 id


 id


 mybutton.is-checked


 is-checked


 Any text you use other than letters, numbers, hyphens, commas, and periods should be encoded via the
 
 encodeURIComponent()
 
 function in JavaScript.




 encodeURIComponent()


**Winget URL:** 

 byond://winget?callback=
 *[callback function]* 
 &id=
 *[control ID/list]* 
 &property=
 *[property/list]* 




**Winget URL:**

 byond://winget?callback=
 *[callback function]* 
 &id=
 *[control ID/list]* 
 &property=
 *[property/list]* 

*[callback function]*
*[control ID/list]*
*[property/list]*

 In this winget, the IDs and properties you want can be separated by commas if you want to retrieve more than one. The winget operation works via a callback function you must define in JavaScript. The callback is given just one argument, a JavaScript object with all of the properties you requested. For example, this URL:




```
byond://winget?callback=wgcb&id=button1&property=is-checked,size,background-color
```


 ...might send this to the callback function wgcb:




```
{
    "is-checked": true,
    "size": {
        "x": 60,
        "y": 20
    },
    "background-color": {
        "value": "none",
        "isDefault": true,
        "red": 236,
        "green": 233,
        "blue": 216,
        "alpha": 255,
        "css": "#ece9d8"
    }
}

```


 The property names will be in the same format you would expect from
 [winget()](#/proc/winget) 
 , so when you're looking at multiple elements' properties, you'll get the full names in
 
 id.property
 
 format. The values are always sent back in a convenient form for JavaScript to work with; in the case of size, position, and color these will always be objects.



[winget()](#/proc/winget)

 id.property


 An optional
 
 control
 
 parameter for the winget call can be used if you want to send data to a callback in a different browser control.




 control



---


