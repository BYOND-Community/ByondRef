

 macros (skin)
---------------



 Macros are used to convert keyboard and gamepad events into actions. There
are two ways this works: A macro can run a command, or in some cases (such as
gamepad controls) it can be used to remap one control to another.




 A collection of macros is called a macro set, and the window currently in
use defines which macro set will be used via its
 [macro](#/{skin}/param/macro) 
 parameter.



[macro](#/{skin}/param/macro)

 Macros can be changed at runtime. If a macro does not have an
 [id](#/{skin}/param/id) 
 , you can refer to it by its key
combination (
 [name](#/{skin}/param/name) 
 ). If you have a
macro set named
 
 macro1
 
 and have a
 
 Ctrl+E
 
 macro for instance,
you could use
 [winset()](#/proc/winset) 
 with
 
 "macro1.Ctrl+E"
 
 . See the
 [Macro
control](#/{skin}/control/macro) 
 for information on which parameters you can change with
 
 winset()
 
 .



[id](#/{skin}/param/id)
[name](#/{skin}/param/name)

 macro1


 Ctrl+E

[winset()](#/proc/winset)

 "macro1.Ctrl+E"

[Macro
control](#/{skin}/control/macro)

 winset()


 The
 
 name
 
 of the macro is actually the full key combination as it
would appear in the macro editor, like
 
 CTRL+E
 
 ,
 
 Space+REP
 
 , or
 
 Alt+Shift+F1
 
 . This is not case-specific and it doesn't matter where
you put modifiers like
 
 CTRL+
 
 ,
 
 SHIFT+
 
 , etc.




 name


 CTRL+E


 Space+REP


 Alt+Shift+F1


 CTRL+


 SHIFT+

### 
 The Any macro



 Oftentimes it's desirable to keep track of key presses yourself rather than
have a hundred different macros defined. BYOND makes this possible via the
 
 Any
 
 and
 
 Any+UP
 
 macros, which respond to any key or gamepad
button.
 
 UP
 
 is the only allowed modifier for this macro, since other
modifier keys are handled by this same macro.




 Any


 Any+UP


 UP


 Typically, you will want to use
 [set
instant=1](#/verb/set/instant) 
 on the verbs that will be tied to the Any macro, so that
keyboard input doesn't queue up and lag behind.



[set
instant=1](#/verb/set/instant)

 In the
 [command](#/{skin}/param/command) 
 that goes with
this macro,
 
 [[\*]]
 
 will be replaced with the name of the key or gamepad
button that was pressed/released. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)



[command](#/{skin}/param/command)

 [[\*]]

[client commands](#/{skin}/commands)

 [[...]]

### 
 Mapping



 The
 [map-to](#/{skin}/param/map-to) 
 parameter is used
by
 **mappings** 
 , which are like macros but are used to convert gamepad
inputs easily and quickly to keyboard inputs. E.g.,
 
 GamepadLeft
 
 can
map to
 
 West
 
 which is the left arrow key. A set of default mappings
will be added automatically at runtime if you don't include any gamepad
mapping in your project.



[map-to](#/{skin}/param/map-to)
**mappings**

 GamepadLeft


 West

### 
 Gamepads



 BYOND will support up to four gamepads, and breaks up their input into the
following categories:



* **Buttons:** 
 Buttons on the controller that are either pressed or not pressed.
* **Directions:** 
 Directions pressed on the D-pad, which act like buttons. Diagonals are also included.
* **D-pad:** 
 The D-pad itself, which can be used to read a
 [dir](#/atom/var/dir) 
 number.
* **Analog:** 
 The analog sticks (BYOND supports left and right).


- **Buttons:** 
 Buttons on the controller that are either pressed or not pressed.

**Buttons:**
- **Directions:** 
 Directions pressed on the D-pad, which act like buttons. Diagonals are also included.

**Directions:**
- **D-pad:** 
 The D-pad itself, which can be used to read a
 [dir](#/atom/var/dir) 
 number.

**D-pad:**
[dir](#/atom/var/dir)
- **Analog:** 
 The analog sticks (BYOND supports left and right).

**Analog:**

 See the list of available macros below for information on how to harness
these inputs.




 To let a user configure their gamepad, you need to call the client-side
 
 .gamepad-mapping
 
[command](#/{skin}/commands) 
 . Or, if they
have access to the Options & Messages window and Dream Seeker's default
menus, they can reach it from there. However it's a good idea to make this
easy for them to find. Several common gamepads are already known by BYOND.




 .gamepad-mapping

[command](#/{skin}/commands)

 There is also the
 
 GamepadRaw
 
 macro, which is similar
to
 
 Any
 
 in some ways and will avoid doing any processing (e.g.
checking for dead zones on the analog sticks) so you can handle all input
yourself.
 
 GamepadRaw
 
 does not rely on BYOND's controller
configuration, so it will not, for instance, know that button 0 should be
 
 GamepadFace1
 
 . See below for more information on how to use this
macro.




 GamepadRaw


 Any


 GamepadRaw


 GamepadFace1

### 
 Mouse macros



 You can add macros (not local player-defined ones) for any of the mouse
input commands, thereby bypassing the normal mouse verbs. This can be helpful
for designing custom setups where you don't want to have to parse the normal
parameter string that provides most of the info, and instead want to provide
data directly to the verb. You will want
 
 set instant=1
 
 on any such
verb.




 set instant=1


 Mouse macro commands use the
 
 [[...]]
 
 syntax to embed values, just
like
 [embedded wingets](#/{skin}/commands) 
 . These are the values you
can include in a mouse macro:




 [[...]]

[embedded wingets](#/{skin}/commands)


| 
 Embedded keyword
  | 
 Meaning
  |
| --- | --- |
| 
 action
  | 
 Name of the mouse action (e.g. MouseDown, MouseMove, etc.).
  |
| 
 src
  | 
 Object the mouse is touching, or dragging/dropping.
  |
| 
 loc
  | 
 Turf or statpanel that
 
 src
 
 is over; in a drag-drop you should split this into
 
 src.loc
 
 and
 
 over.loc
 
 .
  |
| 
 button
  | 
 Mouse button used for this action, if any:
 
 left
 
 ,
 
 middle
 
 , or
 
 right
 
 .
  |
| 
 drag
  | 
 Mouse button currently used for dragging.
  |
| 
 buttons
  | 
 Mouse buttons currently down or involved in this action, separated by commas.
  |
| 
 keys
  | 
 Modifier keys currently held (
 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
 
 ), separated by commas.
  |
| 
 over
  | 
 Object the mouse is over in a drag/drop operation.
  |
| 
 id
  | 
 Control ID; in a drag-drop you should split this into
 
 src.id
 
 and
 
 over.id
 
 .
  |
| 
 icon
  | 
 The icon offset (starting from 1,1 at the lower left) where the mouse action occurred.
 \*  |
| 
 tile
  | 
 The tile where the mouse action occurred, if relevant.
 \*  |
| 
 vis
  | 
 Pixel coordinates relative to the icon's position on screen (same as
 
 icon
 
 but without taking transform into account).
 \*  |
| 
 screen\_loc
  | 
 The regular
 
 screen\_loc
 
 cordinate string.
 \*  |
| 
 screen
  | 
 screen\_loc
 
 coordinates but entirely in pixels starting at 0,0 from lower left.
 \*  |
| 
 screen\_tile
  | 
 screen\_loc
 
 coordinates but only the tile number starting at 1,1.
 \*  |
| 
 screen\_offset
  | 
 screen\_loc
 
 coordinates but only the pixel offset from the tile, starting at 0,0.
 \*  |
| 
 delta
  | 
 Wheel changes in a mouse wheel command.
 \*  |
| 
 left
 
 ,
 
 right
 
 ,
 
 middle
  | 
 1 if this button is down or involved in this action, 0 otherwise
  |
| 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
  | 
 1 if this modifier key is held, 0 otherwise
  |
| 
 link
  | 
 1 if the mouse is over a maptext link, 0 otherwise
  |
| \* 
 Coordinate values are comma-separated, but you can follow them with
 
 .x
 
 or
 
 .y
 
 to get the individual X and Y numbers.
  |


| 
 Embedded keyword
  | 
 Meaning
  |

 
 Embedded keyword
 |
 
 Meaning
 |
| 
 action
  | 
 Name of the mouse action (e.g. MouseDown, MouseMove, etc.).
  |

 
 action
  |

 action

 
 Name of the mouse action (e.g. MouseDown, MouseMove, etc.).
 |
| 
 src
  | 
 Object the mouse is touching, or dragging/dropping.
  |

 
 src
  |

 src

 
 Object the mouse is touching, or dragging/dropping.
 |
| 
 loc
  | 
 Turf or statpanel that
 
 src
 
 is over; in a drag-drop you should split this into
 
 src.loc
 
 and
 
 over.loc
 
 .
  |

 
 loc
  |

 loc

 
 Turf or statpanel that
 
 src
 
 is over; in a drag-drop you should split this into
 
 src.loc
 
 and
 
 over.loc
 
 .
 |

 src


 src.loc


 over.loc

| 
 button
  | 
 Mouse button used for this action, if any:
 
 left
 
 ,
 
 middle
 
 , or
 
 right
 
 .
  |

 
 button
  |

 button

 
 Mouse button used for this action, if any:
 
 left
 
 ,
 
 middle
 
 , or
 
 right
 
 .
 |

 left


 middle


 right

| 
 drag
  | 
 Mouse button currently used for dragging.
  |

 
 drag
  |

 drag

 
 Mouse button currently used for dragging.
 |
| 
 buttons
  | 
 Mouse buttons currently down or involved in this action, separated by commas.
  |

 
 buttons
  |

 buttons

 
 Mouse buttons currently down or involved in this action, separated by commas.
 |
| 
 keys
  | 
 Modifier keys currently held (
 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
 
 ), separated by commas.
  |

 
 keys
  |

 keys

 
 Modifier keys currently held (
 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
 
 ), separated by commas.
 |

 shift


 ctrl


 alt

| 
 over
  | 
 Object the mouse is over in a drag/drop operation.
  |

 
 over
  |

 over

 
 Object the mouse is over in a drag/drop operation.
 |
| 
 id
  | 
 Control ID; in a drag-drop you should split this into
 
 src.id
 
 and
 
 over.id
 
 .
  |

 
 id
  |

 id

 
 Control ID; in a drag-drop you should split this into
 
 src.id
 
 and
 
 over.id
 
 .
 |

 src.id


 over.id

| 
 icon
  | 
 The icon offset (starting from 1,1 at the lower left) where the mouse action occurred.
 \*  |

 
 icon
  |

 icon

 
 The icon offset (starting from 1,1 at the lower left) where the mouse action occurred.
 \*  |
\*
| 
 tile
  | 
 The tile where the mouse action occurred, if relevant.
 \*  |

 
 tile
  |

 tile

 
 The tile where the mouse action occurred, if relevant.
 \*  |
\*
| 
 vis
  | 
 Pixel coordinates relative to the icon's position on screen (same as
 
 icon
 
 but without taking transform into account).
 \*  |

 
 vis
  |

 vis

 
 Pixel coordinates relative to the icon's position on screen (same as
 
 icon
 
 but without taking transform into account).
 \*  |

 icon

\*
| 
 screen\_loc
  | 
 The regular
 
 screen\_loc
 
 cordinate string.
 \*  |

 
 screen\_loc
  |

 screen\_loc

 
 The regular
 
 screen\_loc
 
 cordinate string.
 \*  |

 screen\_loc

\*
| 
 screen
  | 
 screen\_loc
 
 coordinates but entirely in pixels starting at 0,0 from lower left.
 \*  |

 
 screen
  |

 screen

 
 screen\_loc
 
 coordinates but entirely in pixels starting at 0,0 from lower left.
 \*  |

 screen\_loc

\*
| 
 screen\_tile
  | 
 screen\_loc
 
 coordinates but only the tile number starting at 1,1.
 \*  |

 
 screen\_tile
  |

 screen\_tile

 
 screen\_loc
 
 coordinates but only the tile number starting at 1,1.
 \*  |

 screen\_loc

\*
| 
 screen\_offset
  | 
 screen\_loc
 
 coordinates but only the pixel offset from the tile, starting at 0,0.
 \*  |

 
 screen\_offset
  |

 screen\_offset

 
 screen\_loc
 
 coordinates but only the pixel offset from the tile, starting at 0,0.
 \*  |

 screen\_loc

\*
| 
 delta
  | 
 Wheel changes in a mouse wheel command.
 \*  |

 
 delta
  |

 delta

 
 Wheel changes in a mouse wheel command.
 \*  |
\*
| 
 left
 
 ,
 
 right
 
 ,
 
 middle
  | 
 1 if this button is down or involved in this action, 0 otherwise
  |

 
 left
 
 ,
 
 right
 
 ,
 
 middle
  |

 left


 right


 middle

 
 1 if this button is down or involved in this action, 0 otherwise
 |
| 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
  | 
 1 if this modifier key is held, 0 otherwise
  |

 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
  |

 shift


 ctrl


 alt

 
 1 if this modifier key is held, 0 otherwise
 |
| 
 link
  | 
 1 if the mouse is over a maptext link, 0 otherwise
  |

 
 link
  |

 link

 
 1 if the mouse is over a maptext link, 0 otherwise
 |
| \* 
 Coordinate values are comma-separated, but you can follow them with
 
 .x
 
 or
 
 .y
 
 to get the individual X and Y numbers.
  |

 \* 
 Coordinate values are comma-separated, but you can follow them with
 
 .x
 
 or
 
 .y
 
 to get the individual X and Y numbers.
 |
\*

 .x


 .y


 An example mouse macro command might look like this:




> 
> 
> ```
> my-mousedown-verb [[src]] [[button]] "keys=[[keys as params]];drag=[[drag as params]]"
> ```
> 
> 



```
my-mousedown-verb [[src]] [[button]] "keys=[[keys as params]];drag=[[drag as params]]"
```


 In the example, the
 
 src
 
 value is a reference such as you would get
with the
 [ref()
 
 proc](#/proc/ref) 
 . It can be used as a verb
argument directly and won't be enclosed by quotes by default. The
 
 button
 
 value is a string and the default formatting will put quotes around it. The
 
 keys
 
 and
 
 drag
 
 values were given the
 
 as params
 
 format
specifier so they would behave as part of a
 [parameter
list](#/proc/list2params) 
 .




 src

[ref()
 
 proc](#/proc/ref)

 ref()


 button


 keys


 drag


 as params

[parameter
list](#/proc/list2params)

 In drag/drop actions, you can precede any value with
 
 src
 
 or
 
 over
 
 if there may be different information for the dragged object and
the mouseover object/location. This also applies to things like
 
 keys
 
 ,
which by default will be the currently held keys but you can use
 
 src.keys
 
 to refer to the values from when the drag began.




 src


 over


 keys


 src.keys

### 
 Available macros



 This is a list of all keys and gamepad events that can be used in macros.





| **Macro modifiers** 
 are part of the macro name, and control the conditions in which the macro will fire.
  |
| 
 Modifier
  | 
 Meaning
  |
| 
 SHIFT+
  | 
 This macro only counts if either Shift key is pressed.
  |
| 
 CTRL+
  | 
 This macro only counts if either Ctrl key is pressed.
  |
| 
 ALT+
  | 
 This macro only counts if either Alt key is pressed.
  |
| 
 +REP
  | 
 If a key/button is held down, this macro repeats.
  |
| 
 +UP
  | 
 This macro fires when the key/button is released.
  |
| **Keyboard keys** 
 are the garden-variety macros. (This list is abridged to exclude keys probably no one has.)
  |
| 
 Key
  | 
 Description
  |
| 
 A
 
 -
 
 Z
  | 
 Letter key
  |
| 
 0
 
 -
 
 9
  | 
 Number key
  |
| 
 Numpad0
 
 -
 
 Numpad9
  | 
 Numpad numbers
  |
| 
 North
  | 
 Up arrow
  |
| 
 South
  | 
 Down arrow
  |
| 
 East
  | 
 Right arrow
  |
| 
 West
  | 
 Left arrow
  |
| 
 Northwest
  | 
 Home key
  |
| 
 Southwest
  | 
 End key
  |
| 
 Northeast
  | 
 Page Up key
  |
| 
 Southeast
  | 
 Page Down key
  |
| 
 Center
  | 
 Center key (numpad)
  |
| 
 Return
  | 
 Enter / Return key
  |
| 
 Escape
  | 
 Esc key
  |
| 
 Tab
  | 
 Tab key
  |
| 
 Space
  | 
 Space bar
  |
| 
 Back
  | 
 Backspace key
  |
| 
 Insert
  | 
 Ins key
  |
| 
 Delete
  | 
 Del key
  |
| 
 Pause
  | 
 Pause key
  |
| 
 Snapshot
  | 
 Snapshot / Print Screen key
  |
| 
 LWin
  | 
 Left Windows key
  |
| 
 RWin
  | 
 Right Windows key
  |
| 
 Apps
  | 
 Apps key
  |
| 
 Multiply
  | 
 Multiply key
  |
| 
 Add
  | 
 Add key
  |
| 
 Subtract
  | 
 Subtract key
  |
| 
 Divide
  | 
 Divide / Slash key
  |
| 
 Separator
  | 
 Separator / Backslash key
  |
| 
 Shift
  | 
 Shift key (when not used as a modifier)
  |
| 
 Ctrl
  | 
 Ctrl key (when not used as a modifier)
  |
| 
 Alt
  | 
 Alt key (when not used as a modifier)
  |
| 
 VolumeMute
  | 
 Mute key
  |
| 
 VolumeUp
  | 
 Volume up key
  |
| 
 VolumeDown
  | 
 Volume down key
  |
| 
 MediaPlayPause
  | 
 Play/pause media key
  |
| 
 MediaStop
  | 
 Stop media key
  |
| 
 MediaNext
  | 
 Next track key
  |
| 
 MediaPrev
  | 
 Previous track key
  |
| **Special macros**  |
| 
**Any** 
 | 
 A special macro that can run a command on press/release of any key or gamepad button.
 
 UP
 
 is the only modifier allowed. In the command,
 
 [[\*]]
 
 is replaced with the key/button name.
 \*  |
| 
**GamepadRaw** 

\*  | 
 Captures raw input from a gamepad, without regard to the adjustments done by the Gamepad Setup dialog. In the command,
 
 [[id]]
 
 is replaced by the name of the button or axis changed ("Button0" through "Button15" and "Axis0" through "Axis11"),
 
 [[value]]
 
 is replaced with the value of the button or axis, and
 
 [[\*]]
 
 is equivalent to
 
 [[id]] [[value]]
 
 .
  |
| 
\* 
 If no gamepad mappings are included in a game's interface, the default mappings are used instead, which will map the Dpad buttons to the arrow keys. This will cause the Any macro to register both a gamepad directional button and the mapped key on the same press. If you plan on using macros to capture gamepad input, you may wish instead to map any one of the directional buttons to "None", which will override the default gamepad mappings completely.
  |
| **Gamepad buttons** 
† 
 can use another gamepad button as a modifier (but not CTRL, SHIFT, ALT), and can be mapped to one or two keyboard keys or mouse buttons.
  |
| 
 Button
  | 
 Description
  |
| 
 GamepadFace1
  | 
 A (Xbox), X (PS), bottom of diamond
  |
| 
 GamepadFace2
  | 
 B (Xbox), Circle (PS), right of diamond
  |
| 
 GamepadFace3
  | 
 X (Xbox), Square (PS), left of diamond
  |
| 
 GamepadFace4
  | 
 Y (Xbox), Triangle (PS), top of diamond
  |
| 
 GamepadL1
  | 
 Left top shoulder
  |
| 
 GamepadR1
  | 
 Right top shoulder
  |
| 
 GamepadL2
  | 
 Left bottom shoulder
  |
| 
 GamepadR2
  | 
 Right bottom shoulder
  |
| 
 GamepadSelect
  | 
 Select / Back
  |
| 
 GamepadStart
  | 
 Start / Forward
  |
| 
 GamepadL3
  | 
 Left analog click
  |
| 
 GamepadR3
  | 
 Right analog click
  |
| 
 Directional buttons: only one can pressed at a time, and the diagonal buttons are virtual.
  |
| 
 GamepadUp
  | 
 Up button
  |
| 
 GamepadDown
  | 
 Down button
  |
| 
 GamepadLeft
  | 
 Left button
  |
| 
 GamepadRight
  | 
 Right button
  |
| 
 GamepadUpLeft
  | 
 Up+left virtual button
  |
| 
 GamepadUpRight
  | 
 Up+right virtual button
  |
| 
 GamepadDownLeft
  | 
 Down+left virtual button
  |
| 
 GamepadDownRight
  | 
 Down+right virtual button
  |
| **Gamepad analog sticks** 
† 
 can have commands and/or map to
 
 GamepadDir
 
 ,
 
 GamepadDir4
 
 , or
 
 Mouse
 
 . They can use a gamepad button as a modifier. In a command,
 
 [[x]]
 
 and
 
 [[y]]
 
 are replaced by coordinates, and
 
 [[\*]]
 
 is replaced by both with a comma for separation.
  |
| 
 GamepadLeftAnalog
  | 
 Left analog stick
  |
| 
 GamepadRightAnalog
  | 
 Left analog stick
  |
| **Gamepad Dpads** 
†‡ 
 can have commands or are used as mapping targets for analog sticks. A gamepad button can be used as a modifier. In a command,
 
 [[\*]]
 
 is replaced by a direction number, which can be 0.
  |
| 
 GamepadDir
  | 
 Dpad, converted to one of the eight standard directions.
  |
| 
 GamepadDir4
  | 
 Dpad, converted to a cardinal direction.
  |
| 
† 
 All of the gamepad macros defined above apply to the first gamepad. BYOND can now support up to four gamepads, and you can replace Gamepad in the names above with Gamepad2, Gamepad3, or Gamepad4 to access them. Each gamepad also has its own raw macro (i.e., Gamepad2Raw).
 

‡ 
 If you use a Dpad macro like GamepadDir as a
 
 map-to
 
 target, you don't have to specify gamepad 2-4 in map-to; the mapping will automatically know that when Gamepad2LeftAnalog is mapped to GamepadDir, it means Gamepad2Dir.
  |
| **Mouse macros** 
 can have commands but not be used as mapping targets.
  |
| 
 MouseDown
  | 
 Mouse button pressed (replaces MouseDown verb)
  |
| 
 MouseUp
  | 
 Mouse button released (replaces MouseUp verb)
  |
| 
 MouseOver
  | 
 Mouse has moved over a new icon or entered/exited a control (replaces MouseEntered and MouseExited verbs)
  |
| 
 MouseMove
  | 
 Mouse has moved to a new pixel of the same icon (replaces MouseMove verb)
  |
| 
 MouseDrag
  | 
 Mouse has begin dragging or is over a new drop target (replaces MouseDrag verb)
  |
| 
 MouseDragMove
  | 
 Mouse is dragging and is over a new pixel of the same drop target (replaces MouseDrag verb in situations where MouseMove would apply)
  |
| 
 MouseDrop
  | 
 Mouse drag has been released over a target (replaces MouseDrop verb)
  |
| **Mouse targets** 
 can only be used as mapping targets for another macro.
  |
| 
 Mouse
  | 
 The mouse cursor, mappable by a gamepad analog stick.
  |
| 
 MouseLeftButton
  | 
 Left button, mappable by a gamepad button.
  |
| 
 MouseRightButton
  | 
 Right button, mappable by a gamepad button.
  |
| 
 MouseMiddleButton
  | 
 Middle button, mappable by a gamepad button.
  |


| **Macro modifiers** 
 are part of the macro name, and control the conditions in which the macro will fire.
  |
| 
 Modifier
  | 
 Meaning
  |

| **Macro modifiers** 
 are part of the macro name, and control the conditions in which the macro will fire.
  |

 **Macro modifiers** 
 are part of the macro name, and control the conditions in which the macro will fire.
 |
**Macro modifiers**
| 
 Modifier
  | 
 Meaning
  |

 
 Modifier
 |
 
 Meaning
 |
| 
 SHIFT+
  | 
 This macro only counts if either Shift key is pressed.
  |
| 
 CTRL+
  | 
 This macro only counts if either Ctrl key is pressed.
  |
| 
 ALT+
  | 
 This macro only counts if either Alt key is pressed.
  |
| 
 +REP
  | 
 If a key/button is held down, this macro repeats.
  |
| 
 +UP
  | 
 This macro fires when the key/button is released.
  |

| 
 SHIFT+
  | 
 This macro only counts if either Shift key is pressed.
  |

 
 SHIFT+
  |

 SHIFT+

 
 This macro only counts if either Shift key is pressed.
 |
| 
 CTRL+
  | 
 This macro only counts if either Ctrl key is pressed.
  |

 
 CTRL+
  |

 CTRL+

 
 This macro only counts if either Ctrl key is pressed.
 |
| 
 ALT+
  | 
 This macro only counts if either Alt key is pressed.
  |

 
 ALT+
  |

 ALT+

 
 This macro only counts if either Alt key is pressed.
 |
| 
 +REP
  | 
 If a key/button is held down, this macro repeats.
  |

 
 +REP
  |

 +REP

 
 If a key/button is held down, this macro repeats.
 |
| 
 +UP
  | 
 This macro fires when the key/button is released.
  |

 
 +UP
  |

 +UP

 
 This macro fires when the key/button is released.
 |
| **Keyboard keys** 
 are the garden-variety macros. (This list is abridged to exclude keys probably no one has.)
  |
| 
 Key
  | 
 Description
  |

| **Keyboard keys** 
 are the garden-variety macros. (This list is abridged to exclude keys probably no one has.)
  |

 **Keyboard keys** 
 are the garden-variety macros. (This list is abridged to exclude keys probably no one has.)
 |
**Keyboard keys**
| 
 Key
  | 
 Description
  |

 
 Key
 |
 
 Description
 |
| 
 A
 
 -
 
 Z
  | 
 Letter key
  |
| 
 0
 
 -
 
 9
  | 
 Number key
  |
| 
 Numpad0
 
 -
 
 Numpad9
  | 
 Numpad numbers
  |
| 
 North
  | 
 Up arrow
  |
| 
 South
  | 
 Down arrow
  |
| 
 East
  | 
 Right arrow
  |
| 
 West
  | 
 Left arrow
  |
| 
 Northwest
  | 
 Home key
  |
| 
 Southwest
  | 
 End key
  |
| 
 Northeast
  | 
 Page Up key
  |
| 
 Southeast
  | 
 Page Down key
  |
| 
 Center
  | 
 Center key (numpad)
  |
| 
 Return
  | 
 Enter / Return key
  |
| 
 Escape
  | 
 Esc key
  |
| 
 Tab
  | 
 Tab key
  |
| 
 Space
  | 
 Space bar
  |
| 
 Back
  | 
 Backspace key
  |
| 
 Insert
  | 
 Ins key
  |
| 
 Delete
  | 
 Del key
  |
| 
 Pause
  | 
 Pause key
  |
| 
 Snapshot
  | 
 Snapshot / Print Screen key
  |
| 
 LWin
  | 
 Left Windows key
  |
| 
 RWin
  | 
 Right Windows key
  |
| 
 Apps
  | 
 Apps key
  |
| 
 Multiply
  | 
 Multiply key
  |
| 
 Add
  | 
 Add key
  |
| 
 Subtract
  | 
 Subtract key
  |
| 
 Divide
  | 
 Divide / Slash key
  |
| 
 Separator
  | 
 Separator / Backslash key
  |
| 
 Shift
  | 
 Shift key (when not used as a modifier)
  |
| 
 Ctrl
  | 
 Ctrl key (when not used as a modifier)
  |
| 
 Alt
  | 
 Alt key (when not used as a modifier)
  |
| 
 VolumeMute
  | 
 Mute key
  |
| 
 VolumeUp
  | 
 Volume up key
  |
| 
 VolumeDown
  | 
 Volume down key
  |
| 
 MediaPlayPause
  | 
 Play/pause media key
  |
| 
 MediaStop
  | 
 Stop media key
  |
| 
 MediaNext
  | 
 Next track key
  |
| 
 MediaPrev
  | 
 Previous track key
  |

| 
 A
 
 -
 
 Z
  | 
 Letter key
  |

 
 A
 
 -
 
 Z
  |

 A


 Z

 
 Letter key
 |
| 
 0
 
 -
 
 9
  | 
 Number key
  |

 
 0
 
 -
 
 9
  |

 0


 9

 
 Number key
 |
| 
 Numpad0
 
 -
 
 Numpad9
  | 
 Numpad numbers
  |

 
 Numpad0
 
 -
 
 Numpad9
  |

 Numpad0


 Numpad9

 
 Numpad numbers
 |
| 
 North
  | 
 Up arrow
  |

 
 North
  |

 North

 
 Up arrow
 |
| 
 South
  | 
 Down arrow
  |

 
 South
  |

 South

 
 Down arrow
 |
| 
 East
  | 
 Right arrow
  |

 
 East
  |

 East

 
 Right arrow
 |
| 
 West
  | 
 Left arrow
  |

 
 West
  |

 West

 
 Left arrow
 |
| 
 Northwest
  | 
 Home key
  |

 
 Northwest
  |

 Northwest

 
 Home key
 |
| 
 Southwest
  | 
 End key
  |

 
 Southwest
  |

 Southwest

 
 End key
 |
| 
 Northeast
  | 
 Page Up key
  |

 
 Northeast
  |

 Northeast

 
 Page Up key
 |
| 
 Southeast
  | 
 Page Down key
  |

 
 Southeast
  |

 Southeast

 
 Page Down key
 |
| 
 Center
  | 
 Center key (numpad)
  |

 
 Center
  |

 Center

 
 Center key (numpad)
 |
| 
 Return
  | 
 Enter / Return key
  |

 
 Return
  |

 Return

 
 Enter / Return key
 |
| 
 Escape
  | 
 Esc key
  |

 
 Escape
  |

 Escape

 
 Esc key
 |
| 
 Tab
  | 
 Tab key
  |

 
 Tab
  |

 Tab

 
 Tab key
 |
| 
 Space
  | 
 Space bar
  |

 
 Space
  |

 Space

 
 Space bar
 |
| 
 Back
  | 
 Backspace key
  |

 
 Back
  |

 Back

 
 Backspace key
 |
| 
 Insert
  | 
 Ins key
  |

 
 Insert
  |

 Insert

 
 Ins key
 |
| 
 Delete
  | 
 Del key
  |

 
 Delete
  |

 Delete

 
 Del key
 |
| 
 Pause
  | 
 Pause key
  |

 
 Pause
  |

 Pause

 
 Pause key
 |
| 
 Snapshot
  | 
 Snapshot / Print Screen key
  |

 
 Snapshot
  |

 Snapshot

 
 Snapshot / Print Screen key
 |
| 
 LWin
  | 
 Left Windows key
  |

 
 LWin
  |

 LWin

 
 Left Windows key
 |
| 
 RWin
  | 
 Right Windows key
  |

 
 RWin
  |

 RWin

 
 Right Windows key
 |
| 
 Apps
  | 
 Apps key
  |

 
 Apps
  |

 Apps

 
 Apps key
 |
| 
 Multiply
  | 
 Multiply key
  |

 
 Multiply
  |

 Multiply

 
 Multiply key
 |
| 
 Add
  | 
 Add key
  |

 
 Add
  |

 Add

 
 Add key
 |
| 
 Subtract
  | 
 Subtract key
  |

 
 Subtract
  |

 Subtract

 
 Subtract key
 |
| 
 Divide
  | 
 Divide / Slash key
  |

 
 Divide
  |

 Divide

 
 Divide / Slash key
 |
| 
 Separator
  | 
 Separator / Backslash key
  |

 
 Separator
  |

 Separator

 
 Separator / Backslash key
 |
| 
 Shift
  | 
 Shift key (when not used as a modifier)
  |

 
 Shift
  |

 Shift

 
 Shift key (when not used as a modifier)
 |
| 
 Ctrl
  | 
 Ctrl key (when not used as a modifier)
  |

 
 Ctrl
  |

 Ctrl

 
 Ctrl key (when not used as a modifier)
 |
| 
 Alt
  | 
 Alt key (when not used as a modifier)
  |

 
 Alt
  |

 Alt

 
 Alt key (when not used as a modifier)
 |
| 
 VolumeMute
  | 
 Mute key
  |

 
 VolumeMute
  |

 VolumeMute

 
 Mute key
 |
| 
 VolumeUp
  | 
 Volume up key
  |

 
 VolumeUp
  |

 VolumeUp

 
 Volume up key
 |
| 
 VolumeDown
  | 
 Volume down key
  |

 
 VolumeDown
  |

 VolumeDown

 
 Volume down key
 |
| 
 MediaPlayPause
  | 
 Play/pause media key
  |

 
 MediaPlayPause
  |

 MediaPlayPause

 
 Play/pause media key
 |
| 
 MediaStop
  | 
 Stop media key
  |

 
 MediaStop
  |

 MediaStop

 
 Stop media key
 |
| 
 MediaNext
  | 
 Next track key
  |

 
 MediaNext
  |

 MediaNext

 
 Next track key
 |
| 
 MediaPrev
  | 
 Previous track key
  |

 
 MediaPrev
  |

 MediaPrev

 
 Previous track key
 |
| **Special macros**  |

| **Special macros**  |

 **Special macros**  |
**Special macros**
| 
**Any** 
 | 
 A special macro that can run a command on press/release of any key or gamepad button.
 
 UP
 
 is the only modifier allowed. In the command,
 
 [[\*]]
 
 is replaced with the key/button name.
 \*  |
| 
**GamepadRaw** 

\*  | 
 Captures raw input from a gamepad, without regard to the adjustments done by the Gamepad Setup dialog. In the command,
 
 [[id]]
 
 is replaced by the name of the button or axis changed ("Button0" through "Button15" and "Axis0" through "Axis11"),
 
 [[value]]
 
 is replaced with the value of the button or axis, and
 
 [[\*]]
 
 is equivalent to
 
 [[id]] [[value]]
 
 .
  |
| 
\* 
 If no gamepad mappings are included in a game's interface, the default mappings are used instead, which will map the Dpad buttons to the arrow keys. This will cause the Any macro to register both a gamepad directional button and the mapped key on the same press. If you plan on using macros to capture gamepad input, you may wish instead to map any one of the directional buttons to "None", which will override the default gamepad mappings completely.
  |

| 
**Any** 
 | 
 A special macro that can run a command on press/release of any key or gamepad button.
 
 UP
 
 is the only modifier allowed. In the command,
 
 [[\*]]
 
 is replaced with the key/button name.
 \*  |

 
**Any** 
 |

**Any** 

**Any**
 
 A special macro that can run a command on press/release of any key or gamepad button.
 
 UP
 
 is the only modifier allowed. In the command,
 
 [[\*]]
 
 is replaced with the key/button name.
 \*  |

 UP


 [[\*]]

\*
| 
**GamepadRaw** 

\*  | 
 Captures raw input from a gamepad, without regard to the adjustments done by the Gamepad Setup dialog. In the command,
 
 [[id]]
 
 is replaced by the name of the button or axis changed ("Button0" through "Button15" and "Axis0" through "Axis11"),
 
 [[value]]
 
 is replaced with the value of the button or axis, and
 
 [[\*]]
 
 is equivalent to
 
 [[id]] [[value]]
 
 .
  |

 
**GamepadRaw** 

\*  |

**GamepadRaw** 

**GamepadRaw**
\*
 
 Captures raw input from a gamepad, without regard to the adjustments done by the Gamepad Setup dialog. In the command,
 
 [[id]]
 
 is replaced by the name of the button or axis changed ("Button0" through "Button15" and "Axis0" through "Axis11"),
 
 [[value]]
 
 is replaced with the value of the button or axis, and
 
 [[\*]]
 
 is equivalent to
 
 [[id]] [[value]]
 
 .
 |

 [[id]]


 [[value]]


 [[\*]]


 [[id]] [[value]]

| 
\* 
 If no gamepad mappings are included in a game's interface, the default mappings are used instead, which will map the Dpad buttons to the arrow keys. This will cause the Any macro to register both a gamepad directional button and the mapped key on the same press. If you plan on using macros to capture gamepad input, you may wish instead to map any one of the directional buttons to "None", which will override the default gamepad mappings completely.
  |

 
\* 
 If no gamepad mappings are included in a game's interface, the default mappings are used instead, which will map the Dpad buttons to the arrow keys. This will cause the Any macro to register both a gamepad directional button and the mapped key on the same press. If you plan on using macros to capture gamepad input, you may wish instead to map any one of the directional buttons to "None", which will override the default gamepad mappings completely.
  |

\* 
 If no gamepad mappings are included in a game's interface, the default mappings are used instead, which will map the Dpad buttons to the arrow keys. This will cause the Any macro to register both a gamepad directional button and the mapped key on the same press. If you plan on using macros to capture gamepad input, you may wish instead to map any one of the directional buttons to "None", which will override the default gamepad mappings completely.



\*
| **Gamepad buttons** 
† 
 can use another gamepad button as a modifier (but not CTRL, SHIFT, ALT), and can be mapped to one or two keyboard keys or mouse buttons.
  |
| 
 Button
  | 
 Description
  |

| **Gamepad buttons** 
† 
 can use another gamepad button as a modifier (but not CTRL, SHIFT, ALT), and can be mapped to one or two keyboard keys or mouse buttons.
  |

 **Gamepad buttons** 
† 
 can use another gamepad button as a modifier (but not CTRL, SHIFT, ALT), and can be mapped to one or two keyboard keys or mouse buttons.
 |
**Gamepad buttons**
†
| 
 Button
  | 
 Description
  |

 
 Button
 |
 
 Description
 |
| 
 GamepadFace1
  | 
 A (Xbox), X (PS), bottom of diamond
  |
| 
 GamepadFace2
  | 
 B (Xbox), Circle (PS), right of diamond
  |
| 
 GamepadFace3
  | 
 X (Xbox), Square (PS), left of diamond
  |
| 
 GamepadFace4
  | 
 Y (Xbox), Triangle (PS), top of diamond
  |
| 
 GamepadL1
  | 
 Left top shoulder
  |
| 
 GamepadR1
  | 
 Right top shoulder
  |
| 
 GamepadL2
  | 
 Left bottom shoulder
  |
| 
 GamepadR2
  | 
 Right bottom shoulder
  |
| 
 GamepadSelect
  | 
 Select / Back
  |
| 
 GamepadStart
  | 
 Start / Forward
  |
| 
 GamepadL3
  | 
 Left analog click
  |
| 
 GamepadR3
  | 
 Right analog click
  |
| 
 Directional buttons: only one can pressed at a time, and the diagonal buttons are virtual.
  |
| 
 GamepadUp
  | 
 Up button
  |
| 
 GamepadDown
  | 
 Down button
  |
| 
 GamepadLeft
  | 
 Left button
  |
| 
 GamepadRight
  | 
 Right button
  |
| 
 GamepadUpLeft
  | 
 Up+left virtual button
  |
| 
 GamepadUpRight
  | 
 Up+right virtual button
  |
| 
 GamepadDownLeft
  | 
 Down+left virtual button
  |
| 
 GamepadDownRight
  | 
 Down+right virtual button
  |

| 
 GamepadFace1
  | 
 A (Xbox), X (PS), bottom of diamond
  |

 
 GamepadFace1
  |

 GamepadFace1

 
 A (Xbox), X (PS), bottom of diamond
 |
| 
 GamepadFace2
  | 
 B (Xbox), Circle (PS), right of diamond
  |

 
 GamepadFace2
  |

 GamepadFace2

 
 B (Xbox), Circle (PS), right of diamond
 |
| 
 GamepadFace3
  | 
 X (Xbox), Square (PS), left of diamond
  |

 
 GamepadFace3
  |

 GamepadFace3

 
 X (Xbox), Square (PS), left of diamond
 |
| 
 GamepadFace4
  | 
 Y (Xbox), Triangle (PS), top of diamond
  |

 
 GamepadFace4
  |

 GamepadFace4

 
 Y (Xbox), Triangle (PS), top of diamond
 |
| 
 GamepadL1
  | 
 Left top shoulder
  |

 
 GamepadL1
  |

 GamepadL1

 
 Left top shoulder
 |
| 
 GamepadR1
  | 
 Right top shoulder
  |

 
 GamepadR1
  |

 GamepadR1

 
 Right top shoulder
 |
| 
 GamepadL2
  | 
 Left bottom shoulder
  |

 
 GamepadL2
  |

 GamepadL2

 
 Left bottom shoulder
 |
| 
 GamepadR2
  | 
 Right bottom shoulder
  |

 
 GamepadR2
  |

 GamepadR2

 
 Right bottom shoulder
 |
| 
 GamepadSelect
  | 
 Select / Back
  |

 
 GamepadSelect
  |

 GamepadSelect

 
 Select / Back
 |
| 
 GamepadStart
  | 
 Start / Forward
  |

 
 GamepadStart
  |

 GamepadStart

 
 Start / Forward
 |
| 
 GamepadL3
  | 
 Left analog click
  |

 
 GamepadL3
  |

 GamepadL3

 
 Left analog click
 |
| 
 GamepadR3
  | 
 Right analog click
  |

 
 GamepadR3
  |

 GamepadR3

 
 Right analog click
 |
| 
 Directional buttons: only one can pressed at a time, and the diagonal buttons are virtual.
  |

 
 Directional buttons: only one can pressed at a time, and the diagonal buttons are virtual.
 |
| 
 GamepadUp
  | 
 Up button
  |

 
 GamepadUp
  |

 GamepadUp

 
 Up button
 |
| 
 GamepadDown
  | 
 Down button
  |

 
 GamepadDown
  |

 GamepadDown

 
 Down button
 |
| 
 GamepadLeft
  | 
 Left button
  |

 
 GamepadLeft
  |

 GamepadLeft

 
 Left button
 |
| 
 GamepadRight
  | 
 Right button
  |

 
 GamepadRight
  |

 GamepadRight

 
 Right button
 |
| 
 GamepadUpLeft
  | 
 Up+left virtual button
  |

 
 GamepadUpLeft
  |

 GamepadUpLeft

 
 Up+left virtual button
 |
| 
 GamepadUpRight
  | 
 Up+right virtual button
  |

 
 GamepadUpRight
  |

 GamepadUpRight

 
 Up+right virtual button
 |
| 
 GamepadDownLeft
  | 
 Down+left virtual button
  |

 
 GamepadDownLeft
  |

 GamepadDownLeft

 
 Down+left virtual button
 |
| 
 GamepadDownRight
  | 
 Down+right virtual button
  |

 
 GamepadDownRight
  |

 GamepadDownRight

 
 Down+right virtual button
 |
| **Gamepad analog sticks** 
† 
 can have commands and/or map to
 
 GamepadDir
 
 ,
 
 GamepadDir4
 
 , or
 
 Mouse
 
 . They can use a gamepad button as a modifier. In a command,
 
 [[x]]
 
 and
 
 [[y]]
 
 are replaced by coordinates, and
 
 [[\*]]
 
 is replaced by both with a comma for separation.
  |

| **Gamepad analog sticks** 
† 
 can have commands and/or map to
 
 GamepadDir
 
 ,
 
 GamepadDir4
 
 , or
 
 Mouse
 
 . They can use a gamepad button as a modifier. In a command,
 
 [[x]]
 
 and
 
 [[y]]
 
 are replaced by coordinates, and
 
 [[\*]]
 
 is replaced by both with a comma for separation.
  |

 **Gamepad analog sticks** 
† 
 can have commands and/or map to
 
 GamepadDir
 
 ,
 
 GamepadDir4
 
 , or
 
 Mouse
 
 . They can use a gamepad button as a modifier. In a command,
 
 [[x]]
 
 and
 
 [[y]]
 
 are replaced by coordinates, and
 
 [[\*]]
 
 is replaced by both with a comma for separation.
 |
**Gamepad analog sticks**
†

 GamepadDir


 GamepadDir4


 Mouse


 [[x]]


 [[y]]


 [[\*]]

| 
 GamepadLeftAnalog
  | 
 Left analog stick
  |
| 
 GamepadRightAnalog
  | 
 Left analog stick
  |

| 
 GamepadLeftAnalog
  | 
 Left analog stick
  |

 
 GamepadLeftAnalog
  |

 GamepadLeftAnalog

 
 Left analog stick
 |
| 
 GamepadRightAnalog
  | 
 Left analog stick
  |

 
 GamepadRightAnalog
  |

 GamepadRightAnalog

 
 Left analog stick
 |
| **Gamepad Dpads** 
†‡ 
 can have commands or are used as mapping targets for analog sticks. A gamepad button can be used as a modifier. In a command,
 
 [[\*]]
 
 is replaced by a direction number, which can be 0.
  |

| **Gamepad Dpads** 
†‡ 
 can have commands or are used as mapping targets for analog sticks. A gamepad button can be used as a modifier. In a command,
 
 [[\*]]
 
 is replaced by a direction number, which can be 0.
  |

 **Gamepad Dpads** 
†‡ 
 can have commands or are used as mapping targets for analog sticks. A gamepad button can be used as a modifier. In a command,
 
 [[\*]]
 
 is replaced by a direction number, which can be 0.
 |
**Gamepad Dpads**
†‡

 [[\*]]

| 
 GamepadDir
  | 
 Dpad, converted to one of the eight standard directions.
  |
| 
 GamepadDir4
  | 
 Dpad, converted to a cardinal direction.
  |
| 
† 
 All of the gamepad macros defined above apply to the first gamepad. BYOND can now support up to four gamepads, and you can replace Gamepad in the names above with Gamepad2, Gamepad3, or Gamepad4 to access them. Each gamepad also has its own raw macro (i.e., Gamepad2Raw).
 

‡ 
 If you use a Dpad macro like GamepadDir as a
 
 map-to
 
 target, you don't have to specify gamepad 2-4 in map-to; the mapping will automatically know that when Gamepad2LeftAnalog is mapped to GamepadDir, it means Gamepad2Dir.
  |

| 
 GamepadDir
  | 
 Dpad, converted to one of the eight standard directions.
  |

 
 GamepadDir
  |

 GamepadDir

 
 Dpad, converted to one of the eight standard directions.
 |
| 
 GamepadDir4
  | 
 Dpad, converted to a cardinal direction.
  |

 
 GamepadDir4
  |

 GamepadDir4

 
 Dpad, converted to a cardinal direction.
 |
| 
† 
 All of the gamepad macros defined above apply to the first gamepad. BYOND can now support up to four gamepads, and you can replace Gamepad in the names above with Gamepad2, Gamepad3, or Gamepad4 to access them. Each gamepad also has its own raw macro (i.e., Gamepad2Raw).
 

‡ 
 If you use a Dpad macro like GamepadDir as a
 
 map-to
 
 target, you don't have to specify gamepad 2-4 in map-to; the mapping will automatically know that when Gamepad2LeftAnalog is mapped to GamepadDir, it means Gamepad2Dir.
  |

 
† 
 All of the gamepad macros defined above apply to the first gamepad. BYOND can now support up to four gamepads, and you can replace Gamepad in the names above with Gamepad2, Gamepad3, or Gamepad4 to access them. Each gamepad also has its own raw macro (i.e., Gamepad2Raw).
 

‡ 
 If you use a Dpad macro like GamepadDir as a
 
 map-to
 
 target, you don't have to specify gamepad 2-4 in map-to; the mapping will automatically know that when Gamepad2LeftAnalog is mapped to GamepadDir, it means Gamepad2Dir.
  |

† 
 All of the gamepad macros defined above apply to the first gamepad. BYOND can now support up to four gamepads, and you can replace Gamepad in the names above with Gamepad2, Gamepad3, or Gamepad4 to access them. Each gamepad also has its own raw macro (i.e., Gamepad2Raw).



†

‡ 
 If you use a Dpad macro like GamepadDir as a
 
 map-to
 
 target, you don't have to specify gamepad 2-4 in map-to; the mapping will automatically know that when Gamepad2LeftAnalog is mapped to GamepadDir, it means Gamepad2Dir.



‡

 map-to

| **Mouse macros** 
 can have commands but not be used as mapping targets.
  |

| **Mouse macros** 
 can have commands but not be used as mapping targets.
  |

 **Mouse macros** 
 can have commands but not be used as mapping targets.
 |
**Mouse macros**
| 
 MouseDown
  | 
 Mouse button pressed (replaces MouseDown verb)
  |
| 
 MouseUp
  | 
 Mouse button released (replaces MouseUp verb)
  |
| 
 MouseOver
  | 
 Mouse has moved over a new icon or entered/exited a control (replaces MouseEntered and MouseExited verbs)
  |
| 
 MouseMove
  | 
 Mouse has moved to a new pixel of the same icon (replaces MouseMove verb)
  |
| 
 MouseDrag
  | 
 Mouse has begin dragging or is over a new drop target (replaces MouseDrag verb)
  |
| 
 MouseDragMove
  | 
 Mouse is dragging and is over a new pixel of the same drop target (replaces MouseDrag verb in situations where MouseMove would apply)
  |
| 
 MouseDrop
  | 
 Mouse drag has been released over a target (replaces MouseDrop verb)
  |

| 
 MouseDown
  | 
 Mouse button pressed (replaces MouseDown verb)
  |

 
 MouseDown
  |

 MouseDown

 
 Mouse button pressed (replaces MouseDown verb)
 |
| 
 MouseUp
  | 
 Mouse button released (replaces MouseUp verb)
  |

 
 MouseUp
  |

 MouseUp

 
 Mouse button released (replaces MouseUp verb)
 |
| 
 MouseOver
  | 
 Mouse has moved over a new icon or entered/exited a control (replaces MouseEntered and MouseExited verbs)
  |

 
 MouseOver
  |

 MouseOver

 
 Mouse has moved over a new icon or entered/exited a control (replaces MouseEntered and MouseExited verbs)
 |
| 
 MouseMove
  | 
 Mouse has moved to a new pixel of the same icon (replaces MouseMove verb)
  |

 
 MouseMove
  |

 MouseMove

 
 Mouse has moved to a new pixel of the same icon (replaces MouseMove verb)
 |
| 
 MouseDrag
  | 
 Mouse has begin dragging or is over a new drop target (replaces MouseDrag verb)
  |

 
 MouseDrag
  |

 MouseDrag

 
 Mouse has begin dragging or is over a new drop target (replaces MouseDrag verb)
 |
| 
 MouseDragMove
  | 
 Mouse is dragging and is over a new pixel of the same drop target (replaces MouseDrag verb in situations where MouseMove would apply)
  |

 
 MouseDragMove
  |

 MouseDragMove

 
 Mouse is dragging and is over a new pixel of the same drop target (replaces MouseDrag verb in situations where MouseMove would apply)
 |
| 
 MouseDrop
  | 
 Mouse drag has been released over a target (replaces MouseDrop verb)
  |

 
 MouseDrop
  |

 MouseDrop

 
 Mouse drag has been released over a target (replaces MouseDrop verb)
 |
| **Mouse targets** 
 can only be used as mapping targets for another macro.
  |

| **Mouse targets** 
 can only be used as mapping targets for another macro.
  |

 **Mouse targets** 
 can only be used as mapping targets for another macro.
 |
**Mouse targets**
| 
 Mouse
  | 
 The mouse cursor, mappable by a gamepad analog stick.
  |
| 
 MouseLeftButton
  | 
 Left button, mappable by a gamepad button.
  |
| 
 MouseRightButton
  | 
 Right button, mappable by a gamepad button.
  |
| 
 MouseMiddleButton
  | 
 Middle button, mappable by a gamepad button.
  |

| 
 Mouse
  | 
 The mouse cursor, mappable by a gamepad analog stick.
  |

 
 Mouse
  |

 Mouse

 
 The mouse cursor, mappable by a gamepad analog stick.
 |
| 
 MouseLeftButton
  | 
 Left button, mappable by a gamepad button.
  |

 
 MouseLeftButton
  |

 MouseLeftButton

 
 Left button, mappable by a gamepad button.
 |
| 
 MouseRightButton
  | 
 Right button, mappable by a gamepad button.
  |

 
 MouseRightButton
  |

 MouseRightButton

 
 Right button, mappable by a gamepad button.
 |
| 
 MouseMiddleButton
  | 
 Middle button, mappable by a gamepad button.
  |

 
 MouseMiddleButton
  |

 MouseMiddleButton

 
 Middle button, mappable by a gamepad button.
 |


---


