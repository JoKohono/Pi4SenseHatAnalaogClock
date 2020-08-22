# Pi4SenseHatAnalaogClock

Why - what is that?

- I'd like to learn python, git, 
- I have a RPi4 and a SenseHat that I'd like to run in headless mode with following main function:
  - Wireguard VPN (not (yet) relevant here)
  - NAS for my home network (not (yet) relevant here)
  
 The goal is to make the SenseHat as the user interface:
  Output: 
  - analog clock with time 
  - system pixels that provide information about CPU load, f, temp, Memory usage, I/O activity and network status
  
  Input/Control: 
  - via the joystick be able to reboot the Pi (or shut it down)
  - via the joystick rotate the display 
  
Files in the repo: 
The truly only one that matters is the autostart_sensehat.py (which I'm autostarting with the Pi booting through a crontab entry)
The rest is more or less garbage at this point.
Over time a config.txt should come in, too.
Note there is a twin "autostart_senseemu.py" which is set to use the Sense hat emulator. 
but the difference is really just line 3 or 4 which are commented out alternatively. 


SenseHat Output Design Considerations: 

Watchface: 
I don't like digital time telling with a scrolling output; instead want an analog face.
The sensehat however with only 8x8 pixel doesn't allow for a nice clock with hour, minute and seconds hands.
So I went to a design that maps 24hrs to one full circle on the outside: 
- blue pixels at night at the bottom
- green in the morning and evening for "Freizeit" on the sides 
- red throughout the day: the hard working hours.
a blinking LED follows this sun-dial and intuitively indicates the time of the day

another LED for the Minutes makes the round just inside of the hours.

The seconds aren't really important and simply grow from nothing to a smiley in the center as the minute goes on. 

The "eyes" of the smiley are two LEDs that summarize the CPU status (load, f, temp) and the IO status (bytes/sec in and out).

"Issues" are my ideas and tasks to work on over time. And as I hopefully get better with Python,
I'm sure a number of redesigns will go into the coding. 
