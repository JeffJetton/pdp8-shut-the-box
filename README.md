# PDP-8 SHUT THE BOX

A version of the classic pub game [Shut the Box](https://en.wikipedia.org/wiki/Shut_the_box), played entirely on the PDP-8's front panel using the switches and blinkenlights.

No knowledge of binary or octal is required. Anyone can play!

See [the manual](https://github.com/JeffJetton/pdp8-shut-the-box/manual.md)for full instructions.


## Files in the Repo:

* **manual.md**
    * How to play PDP-8 Shut the Box

* **shut.bin**
    * Assembled binary in BIN loader format
 
    
* **shut.pa**
    * PDP-8 assembly language source code, which can be assembled using PAL8 or similar
    * No macros are used, but it currently relies on having off-page links automatically generated



## Adjusting Game Speed

An attempt was made to make the timing of the various light displays work well on a PDP-8 with a speed of around **333,000 instructions-per-second**.

If you are running this in an environment that is noticably slower (a [PDP-8/S](https://gunkies.org/wiki/PDP-8/S), for example) or faster (such as a [PiDP-8](https://obsolescence.dev/pdp8.html) replica running full-out), you'll probably want to make an adjustment.


### Option One: Changing Emulation Speed

On simh, for example, you can throttle the emulation from its command line (ctrl-E):

```
sim>set throttle 333k
sim>continue
```
(You may need to repeat the ctrl-E and `continue` steps to get the speed to finally settle down.)
 

### Option Two: Changing the Game's Internal Speed Parameter

The variable that controls the length of the internal delay loops lives at address `0020` and is set to `7774` in the source code.

You can either edit the source and re-assemble, or just change it on the fly by depositing a new value to `0200`. Use a higher value to speed things up, or a lower value to slow everything down.
