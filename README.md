<img width="2623" height="294" alt="pimmodore small" src="https://github.com/user-attachments/assets/cb971eda-29fb-4416-a16a-242b73965030" />



## A cool way to put a Raspberry Pi 3B inside your Commodore-64 case to run some emulators, or even operative systems.

Pimmodore-64 uses the [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) keyboard interface (Pi Pico) so the keyboard is 100% functional. It's a perfect setup for running [BMC64](https://accentual.com/bmc64/), THE Commodore emulator for the Raspberry Pi 3 (any VICE version works well too). 
Functionally speaking, it's like running an original C-64... or C-128, or Plus/4, or PET Graphics, or PET Business. Keyboard will reconfigure itself, allowing you to access all keys, for ANY of the emulated computers.

Also runs perfectly with any Raspberry Pi Operative System, due to having a PC Compatible layout too.

There is also a [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, able to automatically switch the Compatibility Mode according the computer being emulated, including the color of the RGB LED.

<img width="1565" height="780" alt="foto Pimmodore small" src="https://github.com/user-attachments/assets/0bcf5e63-2465-44ab-b51a-032fdc13c54c" />



<img width="983" height="254" alt="Detalle_trasero-removebg-preview" src="https://github.com/user-attachments/assets/c936121a-ac01-497a-b60c-25dd4d6c299f" />



<img width="668" height="373" alt="detalle_costado-removebg-preview" src="https://github.com/user-attachments/assets/572e6e19-c02b-49ad-ba8e-2bffa1d50175" />




<img width="1336" height="664" alt="image" src="https://github.com/user-attachments/assets/0cfdd3b2-4b19-47ab-afad-4b643fa7f652" />


To build a Pimmodore-64, you need:

- Build a [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) interface first, including the RGB LED.
- A Raspberry Pi 3B o 3B+.
- A MicroSD Card.
- Any power supply greater than 6VDC, with 15 Watts minimum.
- A Step-down Power converter
- Panel Barrel connector
- Rocker switch
- 2 Joysticks connectors (male DB-9)
- Male 4-pole 3.5mm plug, male RCA and female stereo 3.5mm plug (optional for analog outputs).
- HDMI extension cable.
- 2 USB extension cables (or you can buy a USB 2.0 PC rear panel extension bracket)
- A 3D Printer or a 3D Printing service.
- Dupont cables and connectors.
- Some screws.

Look for the .xlsx file for the detailed BOM.

## Printing the STL Files

The pieces are designed to fit any version of the legendary "Breadbin" Commodore-64 case. It won't fit a C-64C (I don't have one to design it).
The project is 100% reversible, no need to drill, make holes or even glue. It uses the same mount system designed for the original PCB board.

There are two versions, with and without analog outputs (not everybody wants to use an old CRT TV...).

You can use an analog VGA 4:3 monitor (maybe a CRT one for a nice vintage look), with a HDMI to VGA adapter. Remember to buy an adapter with analog audio output in case you don't wire the Pi's analog outputs. Although you will have to create some custom HDMI modes, as explained in [BMC64 page](https://github.com/randyrossi/bmc64)

All pieces are easy to print with a 0.4mm nozzle and a 0.2 mm layer height. For better results, do not flip the pieces, print them as provided. The .3mf file was made for my Bambulab A1, in case you find it useful.
There is no need for «Everywhere» support if you 3D Printer is able to do good «bridging» (most printers do). Just use "Normal" support and «Only from the buildplate».
The only piece who need "Tree" support is the USB Ports cover, and just because of the top lock arm, not for the square holes.
The Pico holder includes a little support, where the board back edge rests, just trim it before placing in.

## Flashing and connecting the Keymmodore-64 interface Pi Pico, to the Pi 3B.

At my project [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) you can find detailed information of how to set up a Raspberry Pi Pico as C-64 keyboard interface. 

Besides the cable connecting the keyboard and the RGB LED, there are also three wires from the Pico, they are used for sensing what type of computer is BMC64 emulating. With this information, the Pico can switch to the corresponding mode, avoiding the manual switch with the C= and Function Keys. As you can see, these three pins have to be connected to GPIO 9, 10 and 11 of the R-Pi 3B.
This is not mandatory, if you do not connect those three pins, you can always use the manual switching, including the "PC Compatible Mode".

### This autoswitch feature works only with the [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, it is not included in the oficial release (at least until now).

## Powering the Raspberry Pi

In order to being "agnostic" to the Power Supply, this project uses a Step Down Power Converter, so you can use almost any Power Brick with more than 6V and 15 Watts, a generic 12VDC with 2A will do.
Of course, you need to regulate the Converter BEFORE plug in it to the Raspberry. 5.2VDC will be OK.
Don't try to use a 5VDC power supply directly, the voltage drop of the connector and switch will result in 4.9VDC or less coming into de Pi, therefore the common yellow ligthing bolt sign will appear, and video and audio stuttering will happen, even with "Raspberry Certified Power Supplies". 
Believe me, avoiding the Converter and using a 5VDC Power Supply is not advisable, unless you connect it directly, with no switch in between.

### Remember: Do not plug your Raspberry Pi until you have regulated the Voltage output to 5.2V first!!!!

## Connecting the Joysticks

Unless you have wired the joysticks ports to the Pico interface as mentioned in the Keymmodore-64 project, you can connect them to the Raspberry Pi GPIO pins.

As explained in the [BMC64 website](https://accentual.com/bmc64/), two Atari-like joysticks are supported by the emulator. Here is the wiring according the documentation:

<img width="1024" height="749" alt="image" src="https://github.com/user-attachments/assets/fbf038da-102d-4fc0-ae69-8972fdebb262" />

## Enabling the autoswitching feature

In order to the Pico interface to switch between different modes, you need to connect three wires from the GPIOs Pi to the Pico. The GPIOs to be connected are GPIO 9, 10 and 11, as shown in the Keymmodore readme.

Also, add "enable_pimmodore=1" at the beggining of the cmdline.txt file.

Remember this works only for the modified version of BMC64.

## Connecting the analog video and audio outputs (optional)

The Raspberry Pi 3B includes analog video and stereo audio output. For that you need to wire a 4-pole 3.5mm plug, to a female RCA connector for video, and a miniplug stereo female connector for audio.
BMC64 will output NTSC or PAL-B video standard, according what kind of computer are being emulated.
This is optional. You can use your Pimmodore-64 only with HDMI. There is a .stl version or the frame without the analog outputs for that case. 

Keep in mind, the 4-pole miniplug has this (strange) pinout:

<img width="680" height="567" alt="image" src="https://github.com/user-attachments/assets/83d4f272-d50c-495f-8bae-7efe0149050e" />


## How to set up BMC64 Emulator:

For running BMC64 with the Pi connected to the Pico, you'll need the microSD card with:

1 - The BMC64 Emulator. You can use the modified or the standard BMC64 version, however as explained before, the autoswitching Mode feature won't work in the standard version.

2 - The Kernal ROMs. These are not included in the standard version of BMC64. However you can download from the VICE repository.

3 - The .vkm files in order to have a fully working Keyboard matching all 8-bit emulated computers. Replace the original "positional" .vkm with the new ones.

4 - Enter BMC64 Menu (as explained below), go to "Keyboard" and and change from "Symbolic" to "Positional".

5 - Go to GPIO and check Config is set in "#1 (Nav+Joy)".

6 - Go to Joysticks Menu. If you have wired the joystick ports to the Pi's GPIOs, go to "Joyport" and select GPIO Bank 1 and GPIO Bank 2 for Port 1 and Port 2 respectively. If you have wired the ports to the Pico instead, select Keyset 1 and Keyset 2 and then configure those Keysets below in the same menu.

I strongly recommend to read the [BMC64 readme](https://github.com/randyrossi/bmc64/blob/master/README.md) file for a good understanding of the BMC64 options.

In order to make the whole process easier, I've uploaded a complete version of Lagoela's BMC64 V4.2 autoswitching version, already configured, including the Kernal ROMS and the .vkm files. Joysticks are set as Pi's GPIOs.

I've added HDMI modes for 1080p (HD) monitors and TVs. Both 60Hz for NTSC emulation, and 50 Hz for PAL emulation. I can't tell for every monitor or TV to work OK with 50 Hz, mostly in NTSC-only regions.

Just download, unzip, copy to a FAT32 formatted microSD and boot. 

### Entering the BMC64 Emulator Menu

For entering the BMC64 Menu you need to press CTRL+F7. In PC Compatible Mode (green LED) just press those keys. However, once you are in any Emulator Mode, you can press C= and F7 key for entering the Menu. While browsing the Menu, press Left Arrow Key to go back or exit the Menu. Remember to save the changes before exiting. 

## How to test your keyboard and Joysticks.

I strongly suggest you to use the [Anykey program by T-Pau](https://github.com/T-Pau/Anykey). It has separate versions of programs for every 8 bit Commodore Computer. Very useful. 


## Manual (en español).

I've written a short manual in spanish you can find useful to print (or translate).
















