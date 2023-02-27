

 roll proc
-----------




**See also:** 


[rand proc](#/proc/rand) 



**See also:** 

**See also:**

[rand proc](#/proc/rand) 

[rand proc](#/proc/rand)


**Format:** 


 roll(ndice=1,sides)
 
 roll(dice)
 



**Format:** 

**Format:**

 roll(ndice=1,sides)
 
 roll(dice)
 


 roll(dice)



**Returns:** 


 The sum of the rolled dice.
 


**Returns:** 

**Returns:**

 The sum of the rolled dice.



**Args:** 


 ndice: number of dice to role.
 
 sides: number of sides to the dice.
 
 dice: a text string encoding both ndice and sides (see below).
 




**Args:** 

**Args:**

 ndice: number of dice to role.
 
 sides: number of sides to the dice.
 
 dice: a text string encoding both ndice and sides (see below).
 



 sides: number of sides to the dice.
 
 dice: a text string encoding both ndice and sides (see below).
 


 dice: a text string encoding both ndice and sides (see below).


 The sides of the dice are numbered 1 through the total number of sides
and each is equally likely.




 An alternate form takes the dice parameters in a single text value such
as "3d4". This may be useful when you want to store the dice information in
a single variable. You can even specify an offset, such as "3d4+5". That
adds 5 to the sum of 3 dice having 4 sides each.



### 
 Example:



 obj/potion/healing
 var/dice = "3d6"
 verb/drink()
 var/h = roll(dice)
 if(h>15) usr << "Very refreshing!"
 else usr << "You feel better."



---


