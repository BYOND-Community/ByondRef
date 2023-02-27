

 icon text macro
-----------------




**See also:** 


[icon\_state var (atom)](#/atom/var/icon_state) 

[macros (text)](#/DM/text/macros) 

[style sheets](#/DM/text/style) 

[tags (text)](#/DM/text/tags) 






**See also:** 

**See also:**

[icon\_state var (atom)](#/atom/var/icon_state) 

[macros (text)](#/DM/text/macros) 

[style sheets](#/DM/text/style) 

[tags (text)](#/DM/text/tags) 




[icon\_state var (atom)](#/atom/var/icon_state)

[macros (text)](#/DM/text/macros) 

[style sheets](#/DM/text/style) 

[tags (text)](#/DM/text/tags) 



[macros (text)](#/DM/text/macros)

[style sheets](#/DM/text/style) 

[tags (text)](#/DM/text/tags) 


[style sheets](#/DM/text/style)

[tags (text)](#/DM/text/tags) 

[tags (text)](#/DM/text/tags)

 The \icon macro is used to treat the following embedded
expression (in []'s) as an icon rather than as text. An object, for
example, would be replaced by its icon rather than by its name.



### 
 Example:



 usr << "You look like this: \icon[usr]!"


 The
 `\icon` 
 macro expands internally to the <IMG> tag. The
above example, could be rewritten like this:



`\icon`

 usr << "You look like this: \
 ![](\ref[usr.icon])
 !"

![](\ref[usr.icon])

 Note that the current icon state of the object is automatically used.
Also note that the image belongs to a class called
 `icon` 
 . That
allows you to configure the way icons are displayed by using a style sheet.
The following default style rule causes icons to be shrunk to 16 by 16
pixels so they fit in better with surrounding text:



`icon`

 IMG.icon {width: 16px; height: 16px}


 You could override this setting globally in your own style sheet. You
could even define rules to allow individual icons to be formatted
differently from the rest.



### 
 Example:



 BIG IMG.icon {width: 32px; height: 32px}
SMALL IMG.icon {width: 16px; height: 16px}


 With those rules in place, you could output a full sized icon by using
the <BIG> tag:




 usr << "You look like this:
 
 \icon[usr]
 
 !"


 \icon[usr]


 The one time that one might want to use the <IMG> tag directly is
to specify the ALT text to be displayed on clients which don't support
graphical icons.




 Specific states, directions, and frames of an icon can be displayed in lieu
of the default through use of the following tags:



* ICONSTATE='[state]'
* ICONDIR=[dir], where dir is one of NORTH, SOUTH, EAST, WEST, NORTHEAST, NORTHWEST, SOUTHEAST, SOUTHWEST
* ICONFRAME=[frame], where frame is the animation frame, starting with 1


- ICONSTATE='[state]'

- ICONDIR=[dir], where dir is one of NORTH, SOUTH, EAST, WEST, NORTHEAST, NORTHWEST, SOUTHEAST, SOUTHWEST

- ICONFRAME=[frame], where frame is the animation frame, starting with 1

### 
 Example:



 usr << "You look like this: \
 ![](\ref[usr.icon])
 !"

![](\ref[usr.icon])

 Note that the \icon macro does not work in the mini-browser; it is only
for text output. To make icons appear in an HTML document, use
 [browse\_rsc()](#/proc/browse_rsc) 
 to send an icon to the
client before using
 [browse()](#/proc/browse) 
 to display it.



[browse\_rsc()](#/proc/browse_rsc)
[browse()](#/proc/browse)


---


