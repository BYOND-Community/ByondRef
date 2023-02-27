

 category setting (verb)
-------------------------




**See also:** 


[default\_verb\_category var (client)](#/client/var/default_verb_category) 

[show\_verb\_panel var (client)](#/client/var/show_verb_panel) 




**See also:** 

**See also:**

[default\_verb\_category var (client)](#/client/var/default_verb_category) 

[show\_verb\_panel var (client)](#/client/var/show_verb_panel) 


[default\_verb\_category var (client)](#/client/var/default_verb_category)

[show\_verb\_panel var (client)](#/client/var/show_verb_panel) 

[show\_verb\_panel var (client)](#/client/var/show_verb_panel)


**Format:** 


 set category = "Category"
 


**Format:** 

**Format:**

 set category = "Category"



**Args:** 


 Category: A text string for the category.
 


**Args:** 

**Args:**

 Category: A text string for the category.


 Verbs in the same category are visually grouped together in the verb
panels. The default is "", which is displayed in the default panel titled
"Commands". You can change that default by setting
 `client/default_verb_category` 
 .



`client/default_verb_category`

 To hide a verb from all panels, set the category to null. The verb may
still show up in right-click popup menus, so you may want to use the
 [hidden](#/verb/set/hidden) 
 or
 [popup\_menu](#/verb/set/popup_menu) 
 verb properties instead.



[hidden](#/verb/set/hidden)
[popup\_menu](#/verb/set/popup_menu)


---


