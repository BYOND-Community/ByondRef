

 #define directive
-------------------




**See also:** 


[preprocessor](#/DM/preprocessor) 



**See also:** 

**See also:**

[preprocessor](#/DM/preprocessor) 

[preprocessor](#/DM/preprocessor)


**Format:** 


 #define Name Value
 
 #define Name(Parameters) Value
 



**Format:** 

**Format:**

 #define Name Value
 
 #define Name(Parameters) Value
 


 #define Name(Parameters) Value



**Args:** 


 Name: A macro definition.
 
 Value: The value to substitute for Name.
 
 Parameters: Arguments to pass into the macro.
 




**Args:** 

**Args:**

 Name: A macro definition.
 
 Value: The value to substitute for Name.
 
 Parameters: Arguments to pass into the macro.
 



 Value: The value to substitute for Name.
 
 Parameters: Arguments to pass into the macro.
 


 Parameters: Arguments to pass into the macro.


 The #define statement creates a macro that is substituted for Name.
Substitution only applies to whole words. Text inside of double or single
quotes is not processed for substitution, so
 `"This is BIG."` 
 would
not be modified even if a macro named BIG were defined. That is different
from
 `"This is [BIG]."` 
 , where BIG is an embedded expression, which
does get processed for macro substitution.



`"This is BIG."`
`"This is [BIG]."`
### 
 Example:



 #define DAY 0
#define NIGHT 1
var/daytime = NIGHT //daytime = 1

### 
 Example:



 #define SQR(X) ((X)\*(X))
var/x = SQR(2) //x = ((2)\*(2)) = 4


 Note that it's usually important to use parentheses around any arguments
you use in a macro. Otherwise strange results may occur if you use an
expression such as 2+3. In the SQR(X) example, if there were no parentheses
around each X then the expansion of the macro would be (2+3\*2+3). Since the \*
operator has a higher precedence than + the result is 11, not 25 as expected.
It's equally important to put parentheses around the entire macro for the
same reason.



### 
 Variadic macros



 The last parameter of a macro can end in
 
 ...
 
 which means that it
and all other arguments following it count as a single argument. This is
called a variadic macro because it lets you use a variable number of
arguments. The last parameter will also become optional.




 ...

### 
 Example:



 #define DEFAULT\_LIST(n, items...) if(!n) n = list(items)

### 

 #var
 
 to string



 #var


 In a macro's body, if you precede a parameter by
 
 #
 
 , the
replacement value will be turned into a string. For instance, 2 would become
"2".




 #

### 
 Example:



 #define DEBUG\_VAR(v) world.log << "[#v] = [v]"
DEBUG\_VAR(usr.x) // world.log << "usr.x = [usr.x]"

### 

 ##var
 
 concatenation



 ##var


 A parameter preceded by
 
 ##
 
 in the macro body is substituted
directly, without any spaces. If you use this with the last argument in a
variadic macro, any preceding spaces and a comma (if found) will be removed
if the replacement is empty.




 ##

### 
 Example:



 #define MACROVAR(k) var/macro\_state\_##k
// MACROVAR(right) becomes var/macro\_state\_right

#define PREFIX\_LIST(x, y...) list(x, src, ##y)
// PREFIX\_LIST(1, 2, 3) becomes list(1, src, 2, 3)
// PREFIX\_LIST(4) becomes list(4, src)

### 

 n###var
 
 repeat



 n###var


 Using
 
 ###
 
 in the macro body, preceded by a number, will repeat the
replacement a certain number of times.




 ###

### 
 Example:



 #define SAYTWICE(t) 2###t
#define TOTEXT(t) #t
world << "[TOTEXT(SAYTWICE(hi))]" // world << "hihi"



---


