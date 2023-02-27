

 animate proc
--------------




**See also:** 


[vars (atom)](#/atom/var) 



**See also:** 

**See also:**

[vars (atom)](#/atom/var) 

[vars (atom)](#/atom/var)


**Format:** 


 animate(Object, var1=new\_value1, var2=new\_value2, ..., time, loop, easing, flags, delay)
 
 animate(var1=new\_value1, var2=new\_value2, ..., time, easing, flags, delay)
 
 animate(Object)
 




**Format:** 

**Format:**

 animate(Object, var1=new\_value1, var2=new\_value2, ..., time, loop, easing, flags, delay)
 
 animate(var1=new\_value1, var2=new\_value2, ..., time, easing, flags, delay)
 
 animate(Object)
 



 animate(var1=new\_value1, var2=new\_value2, ..., time, easing, flags, delay)
 
 animate(Object)
 


 animate(Object)



**Args:** 


 Object: The atom, image, or client to animate. (Leave out to do a following animation step on the same object.)
 
 var1=new\_value1, var2=new\_value2, ...: Vars to change in the animation step.
 
 time: Time of this step, in 1/10s. (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 loop: Number of times to show the animation, or -1 to loop forever (may be a named argument)
 
 easing: The "curve" followed by this animation step (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 flags: Flags that impact how the animation acts (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )
 








**Args:** 

**Args:**

 Object: The atom, image, or client to animate. (Leave out to do a following animation step on the same object.)
 
 var1=new\_value1, var2=new\_value2, ...: Vars to change in the animation step.
 
 time: Time of this step, in 1/10s. (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 loop: Number of times to show the animation, or -1 to loop forever (may be a named argument)
 
 easing: The "curve" followed by this animation step (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 flags: Flags that impact how the animation acts (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )
 







 var1=new\_value1, var2=new\_value2, ...: Vars to change in the animation step.
 
 time: Time of this step, in 1/10s. (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 loop: Number of times to show the animation, or -1 to loop forever (may be a named argument)
 
 easing: The "curve" followed by this animation step (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 flags: Flags that impact how the animation acts (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )
 






 time: Time of this step, in 1/10s. (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 loop: Number of times to show the animation, or -1 to loop forever (may be a named argument)
 
 easing: The "curve" followed by this animation step (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 flags: Flags that impact how the animation acts (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )
 




[named argument](#/proc/arguments/named)

 loop: Number of times to show the animation, or -1 to loop forever (may be a named argument)
 
 easing: The "curve" followed by this animation step (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 flags: Flags that impact how the animation acts (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )
 




 easing: The "curve" followed by this animation step (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 flags: Flags that impact how the animation acts (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )
 


[named argument](#/proc/arguments/named)

 flags: Flags that impact how the animation acts (may be a
 [named argument](#/proc/arguments/named) 
 )
 
 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )
 

[named argument](#/proc/arguments/named)

 delay: Delay time for starting the first step in an animation chain (may be negative; may be a
 [named argument](#/proc/arguments/named) 
 )

[named argument](#/proc/arguments/named)

 This proc creates an animation sequence that will be displayed to players.
Starting with an atom or image, you can change one or more vars that affect
its apprearance. This change will take place immediately, but will be
displayed to users as a gradual change over a period of time. The actual
interpolation between frames is all done on the client.




 If the
 
 Object
 
 argument is left out, a new animation step will be
created for the previously used animation seqeunce. If all other arguments are
left out, this is tantamount to saying you want to start a new animation that
does nothing, effectively ending the animation entirely.




 Object

### 
 Example:



 mob/proc/GrowAndFade()
 // expand (scale by 2x2) and fade out over 1/2s
 animate(src, transform = matrix()\*2, alpha = 0, time = 5)

obj/spell/proc/Spin()
 // cast a spell on a monster: make the icon spin
 // this animation takes 3s total (6 ticks \* 5)
 animate(src, transform = turn(matrix(), 120), time = 2, loop = 5)
 animate(transform = turn(matrix(), 240), time = 2)
 animate(transform = null, time = 2)


 The following vars will animate smoothly:



* alpha
* color
* glide\_size
* infra\_luminosity
* layer
* maptext\_width, maptext\_height, maptext\_x, maptext\_y
* luminosity
* pixel\_x, pixel\_y, pixel\_w, pixel\_z
* transform


- alpha

- color

- glide\_size

- infra\_luminosity

- layer

- maptext\_width, maptext\_height, maptext\_x, maptext\_y

- luminosity

- pixel\_x, pixel\_y, pixel\_w, pixel\_z

- transform


 These vars can be changed, but will change immediately on each step rather
than smoothly:



* dir
* icon
* icon\_state
* invisibility
* maptext
* suffix


- dir

- icon

- icon\_state

- invisibility

- maptext

- suffix


 Other vars may apply:



* space: A named var for the
 [color space](#/{{appendix}}/color-space) 
 , if animating color; only applies to non-matrix color values.


- space: A named var for the
 [color space](#/{{appendix}}/color-space) 
 , if animating color; only applies to non-matrix color values.

[color space](#/{{appendix}}/color-space)

 For convenience, you can use an
 [associative list](#/list/associations) 
 , appearance, or
 [mutable appearance](#/mutable_appearance) 
 in place of the appearance
vars. You can use
 
 appearance
 
 itself as a name for this argument, or
leave the argument unnamed.



[associative list](#/list/associations)
[mutable appearance](#/mutable_appearance)

 appearance

### 
 Easing



 Animation doesn't have to be strictly linear. Some changes look much better
if they follow a curve. A cubic curve, for instance, will start slow,
accelerate very quickly in the middle, and slow down again at the end.
A sine curve could be used with a flip transformation to make a coin appear to
spin. A text bubble can jump into place and bounce a little before it settles.
The choice of curve you use is called easing, and you have several good
choices to pick from.
 
 function easing(t,ease,doubled) {
 var \_in=(ease&64), \_out=(ease&128), b; ease &= 63;
 t = Math.max(0,Math.min(1,t)); // clamp t
 if(!ease) return t; // linear case, simplest of all
 if(!\_in && !\_out) { // default case
 switch(ease) {
 case 4: case 5: case 8: \_out = true; break; // bounce, elastic, jump
 default: \_in = \_out = true; break; // all other cases
 }
 }
 if(\_in && \_out) {
 if(ease == 8) return t <= 0.5 ? 0 : 1; // jump is a special case
 return ((t <= 0.5) ? easing(t\*2,ease|64,true) : easing(t\*2-1,ease|128,true)+1) / 2;
 }
 if(\_in) return 1-easing(1-t,ease|128,doubled);
 switch(ease) { // all out cases
 case 1: // sine
 return Math.sin(t\*Math.PI/2);
 case 2: // circular
 t = 1-t; return Math.sqrt(1 - t\*t);
 case 3: // cubic
 t = 1-t; return 1 - t\*t\*t;
 case 4: // bounce
 b = t\*2.75;
 if(b<1) return b\*b; // 1st arc
 if(b<2) {b-=1.5; return b\*b + 0.75;} // bounce #1
 if(b<2.5) {b-=2.25; return b\*b + 0.9375;} // bounce #2
 b-=2.625; return b\*b + 0.984375; // final bounce
 case 5: // elastic
 return 1 - Math.pow(2,-10\*t) \* Math.cos(t\*Math.PI/0.15);
 case 6: // back
 b = doubled ? 2.59491 : 1.70158;
 t = 1-t; return 1 - t\*t\*((b+1)\*t - b);
 case 7: // quad
 t = 1-t; return 1 - t\*t;
 case 8: // jump
 return (t<1) ? 0 : 1;
 default: return t;
 }
}
function drawEasing() {
 var canvas = document.querySelector('#easing\_canvas');
 var ease = document.querySelector('#easing\_type').value;
 if(document.querySelector('#ease\_in').checked) ease |= 64;
 if(document.querySelector('#ease\_out').checked) ease |= 128;
 var ctx=canvas.getContext("2d"), t, y, w=ctx.canvas.width, h=ctx.canvas.height, margin=5, miny=0, maxy=1, s;
 ctx.fillStyle = 'white';
 ctx.fillRect(0,0,w,h);
 ctx.fillStyle = 'transparent';

 w -= margin\*2+1; h -= margin\*2+1;
 for(x=0,y=[]; x<=w; ++x) {
 y[x] = easing(x/w,ease);
 if(y[x] < miny) miny = y[x];
 else if(y[x] > maxy) maxy = y[x];
 }
 s = h / (maxy-miny);

 ctx.beginPath();
 ctx.setLineDash([3,3]); ctx.strokeStyle = 'rgba(0,128,0,0.5)'; ctx.strokeWidth = 1;
 ctx.moveTo(margin, margin+h+miny\*s); ctx.lineTo(margin+w, margin+h+miny\*s);
 ctx.stroke();

 ctx.beginPath();
 ctx.strokeStyle = 'rgba(0,128,255,0.5)';
 ctx.moveTo(margin, margin+(maxy-1)\*s); ctx.lineTo(margin+w, margin+(maxy-1)\*s);
 ctx.stroke();

 ctx.beginPath();
 ctx.setLineDash([]); ctx.strokeStyle = 'black';
 ctx.moveTo(margin, margin+h+miny\*s);
 for(x=1; x<=w; ++x) ctx.lineTo(margin+x, margin+h+(miny-y[x])\*s);
 ctx.stroke();
}
 




 function easing(t,ease,doubled) {
 var \_in=(ease&64), \_out=(ease&128), b; ease &= 63;
 t = Math.max(0,Math.min(1,t)); // clamp t
 if(!ease) return t; // linear case, simplest of all
 if(!\_in && !\_out) { // default case
 switch(ease) {
 case 4: case 5: case 8: \_out = true; break; // bounce, elastic, jump
 default: \_in = \_out = true; break; // all other cases
 }
 }
 if(\_in && \_out) {
 if(ease == 8) return t <= 0.5 ? 0 : 1; // jump is a special case
 return ((t <= 0.5) ? easing(t\*2,ease|64,true) : easing(t\*2-1,ease|128,true)+1) / 2;
 }
 if(\_in) return 1-easing(1-t,ease|128,doubled);
 switch(ease) { // all out cases
 case 1: // sine
 return Math.sin(t\*Math.PI/2);
 case 2: // circular
 t = 1-t; return Math.sqrt(1 - t\*t);
 case 3: // cubic
 t = 1-t; return 1 - t\*t\*t;
 case 4: // bounce
 b = t\*2.75;
 if(b<1) return b\*b; // 1st arc
 if(b<2) {b-=1.5; return b\*b + 0.75;} // bounce #1
 if(b<2.5) {b-=2.25; return b\*b + 0.9375;} // bounce #2
 b-=2.625; return b\*b + 0.984375; // final bounce
 case 5: // elastic
 return 1 - Math.pow(2,-10\*t) \* Math.cos(t\*Math.PI/0.15);
 case 6: // back
 b = doubled ? 2.59491 : 1.70158;
 t = 1-t; return 1 - t\*t\*((b+1)\*t - b);
 case 7: // quad
 t = 1-t; return 1 - t\*t;
 case 8: // jump
 return (t<1) ? 0 : 1;
 default: return t;
 }
}
function drawEasing() {
 var canvas = document.querySelector('#easing\_canvas');
 var ease = document.querySelector('#easing\_type').value;
 if(document.querySelector('#ease\_in').checked) ease |= 64;
 if(document.querySelector('#ease\_out').checked) ease |= 128;
 var ctx=canvas.getContext("2d"), t, y, w=ctx.canvas.width, h=ctx.canvas.height, margin=5, miny=0, maxy=1, s;
 ctx.fillStyle = 'white';
 ctx.fillRect(0,0,w,h);
 ctx.fillStyle = 'transparent';

 w -= margin\*2+1; h -= margin\*2+1;
 for(x=0,y=[]; x<=w; ++x) {
 y[x] = easing(x/w,ease);
 if(y[x] < miny) miny = y[x];
 else if(y[x] > maxy) maxy = y[x];
 }
 s = h / (maxy-miny);

 ctx.beginPath();
 ctx.setLineDash([3,3]); ctx.strokeStyle = 'rgba(0,128,0,0.5)'; ctx.strokeWidth = 1;
 ctx.moveTo(margin, margin+h+miny\*s); ctx.lineTo(margin+w, margin+h+miny\*s);
 ctx.stroke();

 ctx.beginPath();
 ctx.strokeStyle = 'rgba(0,128,255,0.5)';
 ctx.moveTo(margin, margin+(maxy-1)\*s); ctx.lineTo(margin+w, margin+(maxy-1)\*s);
 ctx.stroke();

 ctx.beginPath();
 ctx.setLineDash([]); ctx.strokeStyle = 'black';
 ctx.moveTo(margin, margin+h+miny\*s);
 for(x=1; x<=w; ++x) ctx.lineTo(margin+x, margin+h+(miny-y[x])\*s);
 ctx.stroke();
}



 In this play area, you can test different easing functions to see how they
work.
 



 The horizontal axis from left to right represents the time of the animation
from beginning to end. The vertical axis, from bottom to top, is how the
animation will be interpolated; the lower green line represents the starting
appearance, and the upper blue line is the ending appearance.
 





|  |  |
| --- | --- |
| 

 Progress →
 
 | 
 |
|  | 
 Time →
  |





 LINEAR\_EASING
 

 SINE\_EASING
 

 CIRCULAR\_EASING
 

 CUBIC\_EASING
 

 BOUNCE\_EASING
 

 ELASTIC\_EASING
 

 BACK\_EASING
 

 QUAD\_EASING
 

 JUMP\_EASING
 

  



 EASE\_IN
 
  



 EASE\_OUT
 




 In this play area, you can test different easing functions to see how they
work.




 The horizontal axis from left to right represents the time of the animation
from beginning to end. The vertical axis, from bottom to top, is how the
animation will be interpolated; the lower green line represents the starting
appearance, and the upper blue line is the ending appearance.






|  |  |
| --- | --- |
| 

 Progress →
 
 | 
 |
|  | 
 Time →
  |





 LINEAR\_EASING
 

 SINE\_EASING
 

 CIRCULAR\_EASING
 

 CUBIC\_EASING
 

 BOUNCE\_EASING
 

 ELASTIC\_EASING
 

 BACK\_EASING
 

 QUAD\_EASING
 

 JUMP\_EASING
 

  



 EASE\_IN
 
  



 EASE\_OUT
 




|  |  |
| --- | --- |
| 

 Progress →
 
 | 
 |
|  | 
 Time →
  |


| 

 Progress →
 
 | 
 |

 

 Progress →
 
 |


 Progress →
 


 Progress →

 
 |


|  | 
 Time →
  |

  |
 
 Time →
  |

 Time →




 LINEAR\_EASING
 

 SINE\_EASING
 

 CIRCULAR\_EASING
 

 CUBIC\_EASING
 

 BOUNCE\_EASING
 

 ELASTIC\_EASING
 

 BACK\_EASING
 

 QUAD\_EASING
 

 JUMP\_EASING
 

  



 EASE\_IN
 
  



 EASE\_OUT
 



 LINEAR\_EASING
 

 SINE\_EASING
 

 CIRCULAR\_EASING
 

 CUBIC\_EASING
 

 BOUNCE\_EASING
 

 ELASTIC\_EASING
 

 BACK\_EASING
 

 QUAD\_EASING
 

 JUMP\_EASING
 


 LINEAR\_EASING


 SINE\_EASING


 CIRCULAR\_EASING


 CUBIC\_EASING


 BOUNCE\_EASING


 ELASTIC\_EASING


 BACK\_EASING


 QUAD\_EASING


 JUMP\_EASING

  



 EASE\_IN

  



 EASE\_OUT



 LINEAR\_EASING
 

 Default. Go from one value to another at a constant rate.
 

 SINE\_EASING
 

 The animation follows a sine curve, so it starts off and finishes slowly, with a quicker transition in the middle.
 

 CIRCULAR\_EASING
 

 Similar to a sine curve, but each half of the curve is shaped like a quarter circle.
 

 QUAD\_EASING
 

 A quadratic curve, good for gravity effects.
 

 CUBIC\_EASING
 

 A cubic curve, a little more pronounced than a sine curve.
 

 BOUNCE\_EASING
 

 This transitions quickly like a falling object, and bounces a few times.
   

 Uses
 
 EASE\_OUT
 
 unless otherwise specified.
 

 ELASTIC\_EASING
 

 This transitions quickly and overshoots, rebounds, and finally settles down.
   

 Uses
 
 EASE\_OUT
 
 unless otherwise specified.
 

 BACK\_EASING
 

 Goes a little bit backward at first, and overshoots a little at the end.
 

 JUMP\_EASING
 

 Jumps suddenly from the beginning state to the end. With the default or
 
 EASE\_OUT
 
 , this happens at the end of the time slice. With
 
 EASE\_IN
 
 , the jump happens at the beginning. With both flags set, the jump happens at the halfway point.
 


 LINEAR\_EASING


 Default. Go from one value to another at a constant rate.


 SINE\_EASING


 The animation follows a sine curve, so it starts off and finishes slowly, with a quicker transition in the middle.


 CIRCULAR\_EASING


 Similar to a sine curve, but each half of the curve is shaped like a quarter circle.


 QUAD\_EASING


 A quadratic curve, good for gravity effects.


 CUBIC\_EASING


 A cubic curve, a little more pronounced than a sine curve.


 BOUNCE\_EASING


 This transitions quickly like a falling object, and bounces a few times.
   

 Uses
 
 EASE\_OUT
 
 unless otherwise specified.

  


 EASE\_OUT


 ELASTIC\_EASING


 This transitions quickly and overshoots, rebounds, and finally settles down.
   

 Uses
 
 EASE\_OUT
 
 unless otherwise specified.

  


 EASE\_OUT


 BACK\_EASING


 Goes a little bit backward at first, and overshoots a little at the end.


 JUMP\_EASING


 Jumps suddenly from the beginning state to the end. With the default or
 
 EASE\_OUT
 
 , this happens at the end of the time slice. With
 
 EASE\_IN
 
 , the jump happens at the beginning. With both flags set, the jump happens at the halfway point.


 EASE\_OUT


 EASE\_IN


 These can be combined with
 
 EASE\_IN
 
 or
 
 EASE\_OUT
 
 using the
 
 |
 
 operator, to use just the first or last part of the curve.




 EASE\_IN


 EASE\_OUT


 |

### 
 Example:



 obj/coin/proc/Spin()
 var/matrix/M = matrix()
 M.Scale(-1, 1) // flip horizontally
 animate(src, transform = M, time = 5, loop = 5, easing = SINE\_EASING)
 animate(transform = null, time = 5, easing = SINE\_EASING)

obj/speech\_bubble/New(newloc, msg)
 icon = 'bubble.dmi'

 var/obj/O = new
 O.maptext = msg
 O.maptext\_width = width
 O.maptext\_height = height
 overlays = O

 // start below final position and jump into place
 pixel\_z = -100
 alpha = 0
 animate(src, pixel\_z = 0, alpha = 255, time = 10, easing = ELASTIC\_EASING)


 Some easing functions may overshoot one line or the other, so it's fully
possible to have a
 
 pixel\_w
 
 value, for instance, animate from 0 to 100
but actually end up briefly outside of that range during the animation.




 pixel\_w

### 
 Flags



 Any combination of these flags may be used for animation (use
 
 +
 
 or
 
 |
 
 to combine them):




 +


 |




 ANIMATION\_END\_NOW
 


 Normally if you interrupt another animation, it transitions from its
 current state. This flag will start the new animation fresh by bringing
 the old one to its conclusion. It is only meaningful on the first step
 of a new animation.
 


 ANIMATION\_LINEAR\_TRANSFORM
 


 The transform var is interpolated in a way that preserves size during
 rotation, by pulling the rotation step out. This flag forces linear
 interpolation, which may be more desirable for things like beam effects,
 mechanical arms, etc.
 


 ANIMATION\_PARALLEL
 


 Start a parallel animation sequence that runs alongside the current
 animation sequence. The difference between where the parallel sequence
 started, and its current appearance, is added to the result of any
 previous animations. For instance, you could use this to animate pixel\_y
 separately from pixel\_x with different timing and easing. You could also
 use this to apply a rotational transform after a previous animation
 sequence did a translate. (When using this flag, the src var may be
 included, but it is optional.)
 


 ANIMATION\_RELATIVE
 


 The vars specified are relative to the current state. This works for
 maptext\_x/y/width/height, pixel\_x/y/w/z, luminosity, layer, alpha,
 transform, and color. For transform and color, the current value is
 multiplied by the new one. Vars not in this list are simply changed as
 if this flag is not present. (If you supply an appearance instead of
 individual vars, this flag is meaningless.)
 


 ANIMATION\_CONTINUE
 


 This flag is equivalent to leaving out the
 
 Object
 
 argument.
 It exists to make it easier to define an animation using a
 [for loop](#/proc/for) 
 . If
 
 Object
 
 differs from the
 previous sequence, this flag will be ignored and a new sequence will
 start.
 


 ANIMATION\_SLICE
 


 Following a series of
 
 animate()
 
 calls, you can view just a
 portion of the animation by using
 
 animate(object, delay=start,
 time=duration, flags=ANIMATION\_SLICE)
 
 . The
 
 loop
 
 parameter
 may optionally be included. The
 
 delay
 
 is the start time of the
 slice, relative to the beginning of all the active animations on the
 object. (That is, earlier animations that have concluded will not be
 included.) You can call the proc again with a different slice if you
 want to see a different portion of the animation. A negative value for
 
 time
 
 will remove the slice and finish any existing animations.
 



 ANIMATION\_END\_NOW
 


 ANIMATION\_END\_NOW


 Normally if you interrupt another animation, it transitions from its
 current state. This flag will start the new animation fresh by bringing
 the old one to its conclusion. It is only meaningful on the first step
 of a new animation.



 ANIMATION\_LINEAR\_TRANSFORM
 


 ANIMATION\_LINEAR\_TRANSFORM


 The transform var is interpolated in a way that preserves size during
 rotation, by pulling the rotation step out. This flag forces linear
 interpolation, which may be more desirable for things like beam effects,
 mechanical arms, etc.



 ANIMATION\_PARALLEL
 


 ANIMATION\_PARALLEL


 Start a parallel animation sequence that runs alongside the current
 animation sequence. The difference between where the parallel sequence
 started, and its current appearance, is added to the result of any
 previous animations. For instance, you could use this to animate pixel\_y
 separately from pixel\_x with different timing and easing. You could also
 use this to apply a rotational transform after a previous animation
 sequence did a translate. (When using this flag, the src var may be
 included, but it is optional.)



 ANIMATION\_RELATIVE
 


 ANIMATION\_RELATIVE


 The vars specified are relative to the current state. This works for
 maptext\_x/y/width/height, pixel\_x/y/w/z, luminosity, layer, alpha,
 transform, and color. For transform and color, the current value is
 multiplied by the new one. Vars not in this list are simply changed as
 if this flag is not present. (If you supply an appearance instead of
 individual vars, this flag is meaningless.)



 ANIMATION\_CONTINUE
 


 ANIMATION\_CONTINUE


 This flag is equivalent to leaving out the
 
 Object
 
 argument.
 It exists to make it easier to define an animation using a
 [for loop](#/proc/for) 
 . If
 
 Object
 
 differs from the
 previous sequence, this flag will be ignored and a new sequence will
 start.


 Object

[for loop](#/proc/for)

 Object



 ANIMATION\_SLICE
 


 ANIMATION\_SLICE


 Following a series of
 
 animate()
 
 calls, you can view just a
 portion of the animation by using
 
 animate(object, delay=start,
 time=duration, flags=ANIMATION\_SLICE)
 
 . The
 
 loop
 
 parameter
 may optionally be included. The
 
 delay
 
 is the start time of the
 slice, relative to the beginning of all the active animations on the
 object. (That is, earlier animations that have concluded will not be
 included.) You can call the proc again with a different slice if you
 want to see a different portion of the animation. A negative value for
 
 time
 
 will remove the slice and finish any existing animations.


 animate()


 animate(object, delay=start,
 time=duration, flags=ANIMATION\_SLICE)


 loop


 delay


 time

### 
 Filters



[Filters](#/{notes}/filters) 
 can be animated too. If you want to
animate a filter, you need to specify the filter to be animated. If the last
call to
 
 animate()
 
 used the same object as this filter, or a different
filter for that object, then this will be treated as a new step in the same
animation sequece. Likewise, if the last
 
 animate()
 
 call was to a
filter, and this call is for the object that filter belonged to, again it will
be treated as a continuation of the sequence.



[Filters](#/{notes}/filters)

 animate()


 animate()

### 
 Example:



 atom/proc/BlurFade()
 filters += filter(type = "blur", size = 0)
 // Animating a filter of src
 animate(filters[filters.len], size = 5, time = 10)
 // Switching back to src to animate the next step
 animate(src, alpha = 0, time = 2.5)



---


