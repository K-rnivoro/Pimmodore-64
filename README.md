# Pimmodore-64

Pimmodore-64 is just a cool way to put a Raspberry Pi 3B and the [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) keyboard interface (Pi Pico) inside your Commodore-64 case. It is perfect for running BMC64, THE Commodore emulator for the Raspberry Pi 3. However, any VICE version works well too.

There is also a [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, able to automatically switch the Compatibility Mode according the computer being emulated, including the color of the RGB LED.

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/960b4422-3b1c-4795-b932-7757c56e7850" />

![Imagen de WhatsApp 2025-10-26 a las 15 33 39_1b9a303e](https://github.com/user-attachments/assets/23cd2011-64b7-4886-ab6b-760bd3c4af8d)

<img width="1600" height="738" alt="image" src="https://github.com/user-attachments/assets/3a67bfed-df86-4810-9125-d67cd532ab66" />


![Imagen de WhatsApp 2025-10-26 a las 15 33 40_4545215d](https://github.com/user-attachments/assets/dc6c5dfb-e672-4c16-af87-642def7525f0)


<img width="1336" height="664" alt="image" src="https://github.com/user-attachments/assets/0cfdd3b2-4b19-47ab-afad-4b643fa7f652" />


To build a Pimmodore-64, you need:

- Build a [Keymmodore-64](https://github.com/K-rnivoro/Keymmodore-64) interfase first, including the RGB LED.
- A Raspberry Pi 3B o 3B+.
- A MicroSD Card.
- A 12VDC or greater Power Supply.
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

## Connecting the Keymmodore-64 interface Pi Pico, to the Pi 3B.

Besides the necessary USB cable, there is also three wires from the Pico used for sensing what Computer is BMC64 emulating. With this information, the Pico can switch to the corresponding mode, avoiding the manual switch with Commodore and Functions Keys. As you can see, these three pins have to be connected to GPIO 9, 10 and 11 of the R-Pi 3B.
This is not mandatory, you can always use the manual switching, or even use the "PC Compatible Mode" by pressing Commodore Key and CONTROL.

<img width="707" height="614" alt="image" src="https://github.com/user-attachments/assets/5cd3c5b0-cce0-44af-b48a-b47a405bd97a" />

### This autoswitch feature works only with the [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, it is not included in the oficial release (at least until now).

## Powering the Raspberry Pi

In order to being "agnostic" to the Power Supply, this project uses a Step Down Power Converter, so you can use almost any Power Brick with more than 5V and 15 Watts, a generic 12VDC and 3A will do.
Also, using a Converter, prevents the "voltage drop" of the connector and switch. Being a Step Down, do not use any PS lower than 6V and 3A.
Believe me, I've experimented with 5VDC Power Suplies and I've always had the lighting bolt sign of the Pi, so avoiding the Converter and connecting directly to a 5VDC Power Supply is not advisable (even "Raspberry Certified").
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






















