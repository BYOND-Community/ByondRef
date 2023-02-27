

 SoundQuery proc (client)
--------------------------




**See also:** 


[/sound datum](#/sound) 

[sound proc](#/proc/sound) 




**See also:** 

**See also:**

[/sound datum](#/sound) 

[sound proc](#/proc/sound) 


[/sound datum](#/sound)

[sound proc](#/proc/sound) 

[sound proc](#/proc/sound)


**Format:** 


 SoundQuery()
 


**Format:** 

**Format:**

 SoundQuery()



**Args:** 


 none
 


**Args:** 

**Args:**

 none



**Returns:** 


 A list of
 
 /sound
 
 datums with information about currently playing sounds.
 


**Returns:** 

**Returns:**

 A list of
 
 /sound
 
 datums with information about currently playing sounds.


 /sound


 This proc is used to ask a client about sounds that are playing. The
 
 /sound
 
 datums in the returned list have the following vars set:




 /sound

* file: Sound/music file, or null if none
* channel: Channel of sound, if one was set when the sound was played
* repeat: The
 
 repeat
 
 value of the sound
* status: Status flags active for this channel; currently only
 
 SOUND\_PAUSED
 
 is supported
* offset: Current time index, in seconds, of the sound at the current frequency
* len: Total duration, in seconds, of the sound at the current frequency
* wait: Total duration of sounds queued to play later on this channel (does not apply to channel 0)


- file: Sound/music file, or null if none

- channel: Channel of sound, if one was set when the sound was played

- repeat: The
 
 repeat
 
 value of the sound


 repeat

- status: Status flags active for this channel; currently only
 
 SOUND\_PAUSED
 
 is supported


 SOUND\_PAUSED

- offset: Current time index, in seconds, of the sound at the current frequency

- len: Total duration, in seconds, of the sound at the current frequency

- wait: Total duration of sounds queued to play later on this channel (does not apply to channel 0)


 Not all info about the sounds is retrieved, such as
 
 volume
 
 ,
 
 frequency
 
 , etc. If those are needed, it should be a simple matter to
keep track of them in your code. The main purpose of
 
 SoundQuery()
 
 is
to ascertain the current status of playing sounds.




 volume


 frequency


 SoundQuery()



---


