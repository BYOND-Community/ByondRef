

 operators
-----------




**See also:** 


[operator overloading](#/operator/overload) 



**See also:** 

**See also:**

[operator overloading](#/operator/overload) 

[operator overloading](#/operator/overload)

 Operators are used extensively in DM to compute numerical values.




 The DM operators are:




```
[()](#/operator/()) [.](#/operator/path/%2e) [:](#/operator/path/:) [/](#/operator/path//) [::](#/operator/::)     // here . : / are path operators
[[]](#/operator/[]) [.](#/operator/%2e) [:](#/operator/:)
[?[]](#/operator/%3f[]) [?.](#/operator/%3f%2e) [?:](#/operator/%3f:)
[~](#/operator/~) [!](#/operator/!) [-](#/operator/-) [++](#/operator/++) [--](#/operator/--) [\*](#/operator/*/pointer) [&](#/operator/&/pointer)     // unary operators (\* and & here are pointer operators)
[\*\*](#/operator/**)
[\*](#/operator/*) [/](#/operator//) [%](#/operator/%) [%%](#/operator/%25%25)
[+](#/operator/+) [-](#/operator/-)
[<](#/operator/%3c) [<=](#/operator/%3c=) [>](#/operator/%3e) [>=](#/operator/%3e=)
[<<](#/operator/%3c%3c) [>>](#/operator/%3e%3e)
[==](#/operator/==) [!=](#/operator/!=) [<>](#/operator/%3c%3e) [~=](#/operator/~=) [~!](#/operator/~!)
[&](#/operator/&)
[^](#/operator/^)
[|](#/operator/|)
[&&](#/operator/&&)
[||](#/operator/||)
[?](#/operator/%3f)               // ternary a ? b : c
[=](#/operator/=) [+=](#/operator/+=) [-=](#/operator/-=) [-=](#/operator/-=) [\*=](#/operator/*=) [/=](#/operator//=) [%=](#/operator/%=) [%%=](#/operator/%25%25=) [&=](#/operator/&=) [|=](#/operator/|=) [^=](#/operator/^=) [<<=](#/operator/%3c%3c=) [>>=](#/operator/%3e%3e=) [:=](#/operator/:=) [&&=](#/operator/&&=) [||=](#/operator/||=)
[in](#/operator/in)

```

[()](#/operator/())
[.](#/operator/path/%2e)
[:](#/operator/path/:)
[/](#/operator/path//)
[::](#/operator/::)

 // here . : / are path operators

[[]](#/operator/[])
[.](#/operator/%2e)
[:](#/operator/:)
[?[]](#/operator/%3f[])
[?.](#/operator/%3f%2e)
[?:](#/operator/%3f:)
[~](#/operator/~)
[!](#/operator/!)
[-](#/operator/-)
[++](#/operator/++)
[--](#/operator/--)
[\*](#/operator/*/pointer)
[&](#/operator/&/pointer)

 // unary operators (\* and & here are pointer operators)

[\*\*](#/operator/**)
[\*](#/operator/*)
[/](#/operator//)
[%](#/operator/%)
[%%](#/operator/%25%25)
[+](#/operator/+)
[-](#/operator/-)
[<](#/operator/%3c)
[<=](#/operator/%3c=)
[>](#/operator/%3e)
[>=](#/operator/%3e=)
[<<](#/operator/%3c%3c)
[>>](#/operator/%3e%3e)
[==](#/operator/==)
[!=](#/operator/!=)
[<>](#/operator/%3c%3e)
[~=](#/operator/~=)
[~!](#/operator/~!)
[&](#/operator/&)
[^](#/operator/^)
[|](#/operator/|)
[&&](#/operator/&&)
[||](#/operator/||)
[?](#/operator/%3f)

 // ternary a ? b : c

[=](#/operator/=)
[+=](#/operator/+=)
[-=](#/operator/-=)
[-=](#/operator/-=)
[\*=](#/operator/*=)
[/=](#/operator//=)
[%=](#/operator/%=)
[%%=](#/operator/%25%25=)
[&=](#/operator/&=)
[|=](#/operator/|=)
[^=](#/operator/^=)
[<<=](#/operator/%3c%3c=)
[>>=](#/operator/%3e%3e=)
[:=](#/operator/:=)
[&&=](#/operator/&&=)
[||=](#/operator/||=)
[in](#/operator/in)

 Each line has higher order of operations than the next. Operators within
a line have equal precedence and therefore are processed from left to right
as they occur in an expression. (Assignment, or operate-and-assign, are
processed from right to left.)




 Expressions of the form
 
 A #= B
 
 are shorthand for
 
 A = A # B
 
 except for
 
 ~=
 
 and
 
 :=
 
 .




 A #= B


 A = A # B


 ~=


 :=

### 
 Example:



 var/N
N = 0 // 0
N += 1+1\*2 // 3
if(1 + 1 == 2) N = 2 // 2
if(N==2 && 1/2==0.5) N = 0.5 // 0.5



---


