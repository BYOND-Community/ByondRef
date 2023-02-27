

 sound proc
------------




**See also:** 


[sound datum](#/sound) 

[vars (sound)](#/sound/var) 

[<< output operator](#/operator/%3c%3c/output) 

[load\_resource proc](#/proc/load_resource) 






**See also:** 

**See also:**

[sound datum](#/sound) 

[vars (sound)](#/sound/var) 

[<< output operator](#/operator/%3c%3c/output) 

[load\_resource proc](#/proc/load_resource) 




[sound datum](#/sound)

[vars (sound)](#/sound/var) 

[<< output operator](#/operator/%3c%3c/output) 

[load\_resource proc](#/proc/load_resource) 



[vars (sound)](#/sound/var)

[<< output operator](#/operator/%3c%3c/output) 

[load\_resource proc](#/proc/load_resource) 


[<< output operator](#/operator/%3c%3c/output)

[load\_resource proc](#/proc/load_resource) 

[load\_resource proc](#/proc/load_resource)


**Format:** 


 sound(file,repeat=0,wait,channel,volume)
 

 (supports named arguments)
 




**Format:** 

**Format:**

 sound(file,repeat=0,wait,channel,volume)
 

 (supports named arguments)
 




 (supports named arguments)
 


 (supports named arguments)



**Args:** 


 file: A sound file to play
 
 repeat: 1 to play sound repeatedly
 
 wait: 0 to interrupt current sound on channel; 1 to wait in queue
 
 channel: 0 for any available channel, 1-1024 for specific channel (non-MIDI only)
 
 volume: 100 for full volume (default), 0 for none, or any value in between
 






**Args:** 

**Args:**

 file: A sound file to play
 
 repeat: 1 to play sound repeatedly
 
 wait: 0 to interrupt current sound on channel; 1 to wait in queue
 
 channel: 0 for any available channel, 1-1024 for specific channel (non-MIDI only)
 
 volume: 100 for full volume (default), 0 for none, or any value in between
 





 repeat: 1 to play sound repeatedly
 
 wait: 0 to interrupt current sound on channel; 1 to wait in queue
 
 channel: 0 for any available channel, 1-1024 for specific channel (non-MIDI only)
 
 volume: 100 for full volume (default), 0 for none, or any value in between
 




 wait: 0 to interrupt current sound on channel; 1 to wait in queue
 
 channel: 0 for any available channel, 1-1024 for specific channel (non-MIDI only)
 
 volume: 100 for full volume (default), 0 for none, or any value in between
 



 channel: 0 for any available channel, 1-1024 for specific channel (non-MIDI only)
 
 volume: 100 for full volume (default), 0 for none, or any value in between
 


 volume: 100 for full volume (default), 0 for none, or any value in between


 This is used to play a sound file.




 The sound file must be a music or sample file. Music files include MIDI
(.mid or .midi), and module formats .mod, .it, .s3m, .xm, and .oxm. A sample
file used for sound effects can be .wav, .ogg, .raw, .wma, or .aiff.\*




 The following example plays some sound files. Note that
 `sound()` 
 is not even necessary when you don't need to set any
additional parameters.



`sound()`
### 
 Example:



 usr << 'giggle.wav' // play a giggle once
usr << sound('gigue.midi',1) // repeat gigue
usr << sound('boom.wav', volume=50) // play an explosion at half volume



 \*See
 **Notes** 
 under
 [sound support](#/DM/sound) 
 for
more information.
 




 \*See
 **Notes** 
 under
 [sound support](#/DM/sound) 
 for
more information.

**Notes**
[sound support](#/DM/sound)


---


