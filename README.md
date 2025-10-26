# Pimmodore-64

Pimmodore-64 is just a cool way to put a Raspberry Pi and the Pi Pico inside your Commodore-64 case. It is perfect for running BMC64, THE Commodore emulator for the Raspberry Pi 3. However, any VICE version works well too.

There is also a [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, able to automatically switch the Compatibility Mode according the computer being emulated, including the color of the RGB LED.

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/960b4422-3b1c-4795-b932-7757c56e7850" />

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/2955974c-3fd3-40c9-a21b-1fe33072e57c" />

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/7549ef08-1d7d-40bd-9ea9-e5123a075ba9" />

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

Look the the .xlsx file for the detailed BOM.

## Printing the STL Files

The pieces are designed to fit any version of the legendary "Breadbin" Commodore-64. It won't fit a C-64C (I don't have one to design it).
The project is 100% reversible, no need to drill, glue or make holes. It uses the same mount holes than the original PCB board.

All pieces are easy to print with a 0.4mm nozzle and a 0.2 mm layer height. For better results, do not rotate the pieces, print them as provided.
There is no need for «Everywhere» support if you 3D Printer is able to do good «bridging» (most printers do). Just use support «Only from the buildplate», except for the USB Ports who needs «Everywhere support», and just because of the lock arms, not for the holes.

## Connecting the Raspberry Pi 3B to the Pi Pico Interfase.

Besides the necessary USB cable, there is also three wires from the Pico used for sensing what Computer is BMC64 emulating. With this information, the Pico can switch to the corresponding mode, avoiding the manual switch with Commodore and Functions Keys. As you can see, these three pins have to be connected to GPIO 9, 10 and 11 of the R-Pi 3B.
This is not mandatory, you can always use the manual switching, or even use the "PC Compatible Mode" by pressing Commodore Key and CONTROL.

<img width="707" height="614" alt="image" src="https://github.com/user-attachments/assets/5cd3c5b0-cce0-44af-b48a-b47a405bd97a" />

### This autoswitch feature works only with the [modified version of BMC64](https://github.com/slagoela/bmc64) made by Sergio Lagoela, it is not included in the oficial release (at least until now).

## Powering the Raspberry Pi

In order to being "agnostic" to the Power Supply, this project uses a Step Down Power Converter, so you can use almost any Power Brick with more than 5V and 15 Watts, a generic 12VDC and 3A will do.
Also, using a Converter, prevents the "voltage drop" of the connector and switch. Believe me, I've experimented with 5VDC Power Supllies and I've always had the lighting bolt sign of the Pi, so connecting directly to a 5VDC Power Supply is not advisable (even "Raspberry Certified"). Also, being a Step Down, do not use any PS lower than 6V!
### Do not plug your Raspberry Pi until you have regulated the Voltage output to 5.2V !!!!

## Connecting the Joysticks

As explained in the [BMC64 website](https://accentual.com/bmc64/), two Atari-like joysticks are supported by the emulator. Here is the wiring according the documentation:

<img width="1024" height="749" alt="image" src="https://github.com/user-attachments/assets/fbf038da-102d-4fc0-ae69-8972fdebb262" />














