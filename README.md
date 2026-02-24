<img width="1200" height="150" alt="PImmodore-64" src="https://github.com/user-attachments/assets/166db84b-37bb-4b89-bb54-b0b4eb1b4c45" />

## A cool way to put a Raspberry Pi 3B inside your Commodore-64 case.

Pimmodore-64 uses the [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) keyboard interface (Pi Pico) so the keyboard is 100% functional. It's a perfect setup for running [BMC64](https://accentual.com/bmc64/), THE Commodore emulator for the Raspberry Pi 3 (any VICE version works well too).
Functionally speaking, it's like running an original C-64... or C-128, or Plus/4, or PET Graphics, or PET Business. Keyboard will reconfigure itself, allowing you to access all keys, for ANY of the emulated computers. 

There is also a [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, able to automatically switch the Compatibility Mode according the computer being emulated, including the color of the RGB LED.

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/960b4422-3b1c-4795-b932-7757c56e7850" />

![Detalle trasero](https://github.com/user-attachments/assets/cd444970-57af-4e29-af0e-3bd7a801e7b9)


![fotos consola-26](https://github.com/user-attachments/assets/19f236e3-c035-452e-86e8-feb3abb3660d)


<img width="1336" height="664" alt="image" src="https://github.com/user-attachments/assets/0cfdd3b2-4b19-47ab-afad-4b643fa7f652" />


To build a Pimmodore-64, you need:

- Build a [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) interface first, including the RGB LED.
- A Raspberry Pi 3B o 3B+.
- A MicroSD Card.
- Any power supply greater than 6VDC, with 15 Watts minimum.
- A Step Down Power converter
- Power connector and switch
- Joysticks connectors
- Analog Audio and Video connectors (optional).
- HDMI extension cable.
- 2 USB extension cables.
- A 3D Printer or a 3D Printing service.
- Dupont cables and connectors.
- Some screws.

Look for the .xlsx file for the detailed BOM.

## Printing the STL Files

The pieces are designed to fit any version of the legendary "Breadbin" Commodore-64 case. It won't fit a C-64C (I don't have one to design it).
The project is 100% reversible, no need to drill, make holes or even glue. It uses the same mount system designed for the original PCB board.

All pieces are easy to print with a 0.4mm nozzle and a 0.2 mm layer height. For better results, do not rotate the pieces, print them as provided.
There is no need for «Everywhere» support if you 3D Printer is able to do good «bridging» (most printers do). Just use support «Only from the buildplate», except for the USB Ports who needs «Everywhere support», and just because of the lock arms, not for the holes.
The Pico holder has two little support arms where the back edge of the board rests, just cut them before placing in.

## Flashing and connecting the Keymmodore-64 interface Pi Pico, to the Pi 3B.

In my project [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) you can find detailed information how to set up a Raspberry Pi Pico as a keyboard interface. 

Besides the cable connecting the keyboard and the RGB LED, there are also three wires from the Pico, they are used for sensing what Computer is BMC64 emulating. With this information, the Pico can switch to the corresponding mode, avoiding the manual switch with the C= and Function Keys. As you can see, these three pins have to be connected to GPIO 9, 10 and 11 of the R-Pi 3B.
This is not mandatory, if you do not connect those three pins, you can always use the manual switching, including the "PC Compatible Mode".

### This autoswitch feature works only with the [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, it is not included in the oficial release (at least until now).

## Powering the Raspberry Pi

In order to being "agnostic" to the Power Supply, this project uses a Step Down Power Converter, so you can use almost any Power Brick with more than 6V and 15 Watts, a generic 12VDC with 2A will do.
Of course, you need to regulate the Converter BEFORE plug in it to the Raspberry. 5.2VDC will be OK.
Don't try to use a 5VDC power supply directly, the voltage drop of the connector and switch will result in 4.9VDC or less coming into de Pi, therefore the common "yellow ligthing bolt" will appear, and video and audio suttering will happen, even with "Raspberry Certified Power Supplies" 
Believe me, avoiding the Converter and using a 5VDC Power Supply is not advisable, unless you connect it directly, with no barrel plug and switch in between.

### Remember: Do not plug your Raspberry Pi until you have regulated the Voltage output to 5.2V first!!!!

## Connecting the Joysticks

Unless you have wired the joysticks ports to the Pi interface as mentioned in the Keymmodore-64 project, you can use the option of connecting them to the Raspberry Pi GPIO pins.

As explained in the [BMC64 website](https://accentual.com/bmc64/), two Atari-like joysticks are supported by the emulator. Here is the wiring according the documentation:

<img width="1024" height="749" alt="image" src="https://github.com/user-attachments/assets/fbf038da-102d-4fc0-ae69-8972fdebb262" />


## Connecting the analog video and audio outputs

The Raspberry Pi 3B includes analog video and stereo audio output. For that you need to wire a 4-pole 3.5mm plug, to a female RCA connector for video, and a miniplug stereo female connector for audio.
BMC64 will output NTSC or PAL-B video standard, according what kind of computer are being emulated.

Keep in mind, the 4-pole miniplug has this (strage) pinout:

<img width="680" height="567" alt="image" src="https://github.com/user-attachments/assets/83d4f272-d50c-495f-8bae-7efe0149050e" />


## Setting up the BMC64 Emulator

You can use the standard BMC64 version or any other Emulator with your Pimmodore-64, however as explained before, the autoswitching Mode feature won't work. Also, for BMC64 (regardless it's version) you'll need the Kernal's ROMs.

As explained in the Keymmodore-64 project, the correct .vkm files are necessary in order to have a fully working C-64 Keyboard for all 8-bit Computers able to emulate. Download them from [here](https://github.com/K-rnivoro/Keymmodore-64/blob/master/BMC64%20VKM.zip).

In order to make the whole process easier, I've uploaded a complete version of Lagoela's BMC64 autoswitching version, including the ROMS and the VKM files. So you only need to setup a few things.
However, I strongly recommend to read the [BMC64 readme](https://github.com/randyrossi/bmc64/blob/master/README.md) file for a good understanding of the BMC64 options.






















