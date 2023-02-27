

 grid control (skin)
---------------------



 A grid that contains multiple cells that can show various kinds of output data.





**Grid-specific parameters:** 


[cell-span](#/{skin}/param/cell-span) 

[cells](#/{skin}/param/cells) 

[current-cell](#/{skin}/param/current-cell) 

[enable-http-images](#/{skin}/param/enable-http-images) 

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 















**Grid-specific parameters:** 

**Grid-specific parameters:**

[cell-span](#/{skin}/param/cell-span) 

[cells](#/{skin}/param/cells) 

[current-cell](#/{skin}/param/current-cell) 

[enable-http-images](#/{skin}/param/enable-http-images) 

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 













[cell-span](#/{skin}/param/cell-span)

[cells](#/{skin}/param/cells) 

[current-cell](#/{skin}/param/current-cell) 

[enable-http-images](#/{skin}/param/enable-http-images) 

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 












[cells](#/{skin}/param/cells)

[current-cell](#/{skin}/param/current-cell) 

[enable-http-images](#/{skin}/param/enable-http-images) 

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 











[current-cell](#/{skin}/param/current-cell)

[enable-http-images](#/{skin}/param/enable-http-images) 

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 










[enable-http-images](#/{skin}/param/enable-http-images)

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 









[highlight-color](#/{skin}/param/highlight-color)

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 








[is-list](#/{skin}/param/is-list)

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 







[line-color](#/{skin}/param/line-color)

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 






[link-color](#/{skin}/param/link-color)

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 





[show-lines](#/{skin}/param/show-lines)

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 




[show-names](#/{skin}/param/show-names)

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 



[small-icons](#/{skin}/param/small-icons)

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 


[style](#/{skin}/param/style)

[visited-color](#/{skin}/param/visited-color) 

[visited-color](#/{skin}/param/visited-color)

 Sending output to a grid looks like this:



### 
 Example:



 // output to column 3, row 2
winset(usr, "thegrid", "current-cell=3,2")
usr << output("Text", "thegrid")

// or even easier:
usr << output("Text", "thegrid:3,2")

// when is-list is true:
usr << output("5th item", "thegrid:5")


 You can output an atom to the grid, which can be clicked, dragged, etc.
However, you should make sure that atom is
 *not* 
 temporary and will
persist until you no longer need it, or else the server may recycle it and
the object in the cell will either disappear or be impossible to interact
with anymore.



*not*

 There are some limitations to output in grid controls:



* Only one character style (font, color, bold, etc.) may appear within a single cell.
* A cell is either a link, or not.
* One image is allowed per cell.
* A cell can hold an object (atom), sent to it via the
 [output()
 
 proc](#/proc/output) 
 , which can be clicked, dragged, etc.; it will not act as a link.
* The same margin is used all around the cell, not different margins for left, right, top, bottom.
* There will always be a 1-pixel space for grid lines, whether they're shown or not.


- Only one character style (font, color, bold, etc.) may appear within a single cell.

- A cell is either a link, or not.

- One image is allowed per cell.

- A cell can hold an object (atom), sent to it via the
 [output()
 
 proc](#/proc/output) 
 , which can be clicked, dragged, etc.; it will not act as a link.

[output()
 
 proc](#/proc/output)

 output()

- The same margin is used all around the cell, not different margins for left, right, top, bottom.

- There will always be a 1-pixel space for grid lines, whether they're shown or not.



---


