

 MeasureText proc (client)
---------------------------




**See also:** 


[maptext var (atom)](#/atom/var/maptext) 

[maptext\_width var (atom)](#/atom/var/maptext_width) 

[maptext\_height var (atom)](#/atom/var/maptext_height) 





**See also:** 

**See also:**

[maptext var (atom)](#/atom/var/maptext) 

[maptext\_width var (atom)](#/atom/var/maptext_width) 

[maptext\_height var (atom)](#/atom/var/maptext_height) 



[maptext var (atom)](#/atom/var/maptext)

[maptext\_width var (atom)](#/atom/var/maptext_width) 

[maptext\_height var (atom)](#/atom/var/maptext_height) 


[maptext\_width var (atom)](#/atom/var/maptext_width)

[maptext\_height var (atom)](#/atom/var/maptext_height) 

[maptext\_height var (atom)](#/atom/var/maptext_height)


**Format:** 


 MeasureText(text, style, width=0)
 


**Format:** 

**Format:**

 MeasureText(text, style, width=0)



**Args:** 


 text: The text to be measured
 
 style: Stylesheet to be used (leave blank to use the default map control's styles, if any)
 
 width: Width limit, if you only want to measure height; 0 means no limit
 




**Args:** 

**Args:**

 text: The text to be measured
 
 style: Stylesheet to be used (leave blank to use the default map control's styles, if any)
 
 width: Width limit, if you only want to measure height; 0 means no limit
 



 style: Stylesheet to be used (leave blank to use the default map control's styles, if any)
 
 width: Width limit, if you only want to measure height; 0 means no limit
 


 width: Width limit, if you only want to measure height; 0 means no limit



**Returns:** 


 A size value in
 
 "[width]x[height]"
 
 format, e.g. "60x16"
 


**Returns:** 

**Returns:**

 A size value in
 
 "[width]x[height]"
 
 format, e.g. "60x16"


 "[width]x[height]"


 Because maptext rendering may vary by client,
 
 MeasureText
 
 lets
you get a measurement of how text will be laid out, so you can adjust
 
 maptext\_width
 
 and
 
 maptext\_height
 
 accordingly.




 MeasureText


 maptext\_width


 maptext\_height



---


