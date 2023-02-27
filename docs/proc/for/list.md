

 for list proc
---------------




**See also:** 


[for loop proc](#/proc/for/loop) 

[list](#/list) 

[istype](#/proc/istype) 





**See also:** 

**See also:**

[for loop proc](#/proc/for/loop) 

[list](#/list) 

[istype](#/proc/istype) 



[for loop proc](#/proc/for/loop)

[list](#/list) 

[istype](#/proc/istype) 


[list](#/list)

[istype](#/proc/istype) 

[istype](#/proc/istype)


**Format:** 


 for (Var [as Type] [in List]) Statement
 
 for (Var in Start to End [step Step]) Statement
 



**Format:** 

**Format:**

 for (Var [as Type] [in List]) Statement
 
 for (Var in Start to End [step Step]) Statement
 


 for (Var in Start to End [step Step]) Statement



**Args:** 


 Var: A variable to sequentially contain each member of the list.
 
 List: The list to loop through. This defaults to the whole world.
 
 Type: One or more of area, turf, mob, or obj, ORed together. If no
 type is specified, the declared type of Var will be used to skip over
 inappropriate elements in the list.
 
 Start: A starting numeric value.
 
 End: An ending numeric value (inclusive).
 
 Step: An increment for the numeric value; default is 1.
 







**Args:** 

**Args:**

 Var: A variable to sequentially contain each member of the list.
 
 List: The list to loop through. This defaults to the whole world.
 
 Type: One or more of area, turf, mob, or obj, ORed together. If no
 type is specified, the declared type of Var will be used to skip over
 inappropriate elements in the list.
 
 Start: A starting numeric value.
 
 End: An ending numeric value (inclusive).
 
 Step: An increment for the numeric value; default is 1.
 






 List: The list to loop through. This defaults to the whole world.
 
 Type: One or more of area, turf, mob, or obj, ORed together. If no
 type is specified, the declared type of Var will be used to skip over
 inappropriate elements in the list.
 
 Start: A starting numeric value.
 
 End: An ending numeric value (inclusive).
 
 Step: An increment for the numeric value; default is 1.
 





 Type: One or more of area, turf, mob, or obj, ORed together. If no
 type is specified, the declared type of Var will be used to skip over
 inappropriate elements in the list.
 
 Start: A starting numeric value.
 
 End: An ending numeric value (inclusive).
 
 Step: An increment for the numeric value; default is 1.
 




 Start: A starting numeric value.
 
 End: An ending numeric value (inclusive).
 
 Step: An increment for the numeric value; default is 1.
 



 End: An ending numeric value (inclusive).
 
 Step: An increment for the numeric value; default is 1.
 


 Step: An increment for the numeric value; default is 1.

### 
 Example:



 usr << "Mobs:"
var/mob/M
for(M in view())
 usr << M.name


 This loops M through the mobs in view(), outputting the name at each
iteration.




 When you loop through a list, with the exception of looping through
world, you're actually looping through a copy of that list. If the list
changes, those changes won't have any bearing on this loop. If you want to
be able to handle a list that might change, you'll need to use the
 [for loop proc](#/proc/for/loop) 
 instead.



[for loop proc](#/proc/for/loop)

 You can declare the variable right inside the for statement. Its scope
is entirely contained within the for statement, so it will not conflict with
a similar variable declared elsewhere in the same procedure.



### 
 Example:



 client/verb/who()
 for(var/client/Player)
 usr << Player


 If the loop var has a type, a hidden
 
 istype()
 
 call is included in
the code. Only items of that type, or its descendants, are handled within the
loop. That means null values and objects of unrelated types will be skipped.




 istype()


 The numeric loop form is a quick internal version of the
 [for loop proc](#/proc/for/loop) 
 . It's equivalent to
 
 for(Var = Start, Var <= End, Var += Step)
 
 unless Step is
negative, in which case a >= comparison is used instead. The main
difference is that unlike in a for loop proc, the values of Step and
End are calculated at the beginning and never change after that, so an
expression like
 
 list.len
 
 that might be subject to change will not be
read again—in much the same way that looping through a list only loops
through a copy of that list.



[for loop proc](#/proc/for/loop)

 for(Var = Start, Var <= End, Var += Step)


 list.len

### 
 Example:



 for(var/count in 1 to 100)
 src << count


 Note: Although you can use fractional values for
 
 step
 
 in this
numeric format, there may be accuracy considerations to keep in mind. See
 [Numbers](#/{notes}/numbers) 
 for more information.




 step

[Numbers](#/{notes}/numbers)


---


