# Pocket65

Handheld PC based on the original 6502 CPU that fits into a pocket.

## Features

- 8 digit multiplexed 7-segment display,
- 24 button keyboard,
- 2 KB of ROM and 2 KB of RAM,
- built-in Li-Po power supply and charger,
- monitor FW that allows memory edit and running user programs,
- expansion slot with 3 chip selects (up to 24 KB of external I/O and/or memory).

# Monitor how-to

## Startup

First, welcome splash-screen is displayed:

![welcome screen](img/welcome.png)

After one second memory test result is displayed:

![memory test result](img/memtest.png)

On the right is a decimal number of RAM bytes found. By default it's 2048 bytes, memory can be expanded using expansion slot. If an error occurs during memory test, error screen is presented and the system is halted:

![memory test fail](img/memfail.png)

After 2 seconds computer proceeds to the main mode of operation:

![monitor](img/main.png)

## Memory edit

In the main mode and byte modification selected (dot near memory value) memory modification is possible. To modify memory press a key `0` to `F`. The old value is then shifted 4 binary places to the left and new nibble is inserted at the youngest position. Previous 4 oldest bits are lost.

Example - entering `0xBA` at current address:

We start with our memory cell selected (in this case at the address `0x0200`):

![memory edit start](img/main.png)

press `B` button to enter 0xB:

![b pressed](img/memedit1.png)

then press `A` button to finish entering the byte:

![a pressed](img/memedit2.png)

Done!

## Address selection

The address can be modified in two ways:

### INC/DEC buttons

To select next/prev memory cell press `INC`/`DEC` button. The address will be incremented/decremented by one.

### Entering new address

Big leaps through memory space are not very convenient using incrementation/decrementation. You can change the address very similar to changing memory value. To enter address edit mode pres `SEL` key. Dot will appear next to address to confirm mode selection:

![address edit mode](img/seladdr.png)

In this mode address can be modified the same way memory value is performed - when key `0-F` is pressed the old address is shifted 4 bits to the left and new value is inserted at the youngest position.

To exit address edit mode (and return to the memory value edit mode) press `SEL` key.

## Executing user program

To start user program provides its entry point in the address field and press `GO` button.

## F1 key - auto increment mode

`F1` key toggles auto-increment mode. When on it's indicated by dots enabled next to both address and value:

![autoincrement mode](img/autoinc.png)

When this mode is active when the whole byte is entered (i.e. two key `0-F` presses) address will be incremented automatically. This mode is very useful for binary program listing input, as no additional key press between bytes is needed.

## F2 key - memory clear

`F2` key clears user memory - sets it to all zeroes. Memory locations from `0x0000` to `0x000CF` and from `0x2000` to RAM end are cleared.

## F3 key - memory copy

`F3` key copies _length_ bytes from _source_ to _destination_. _Destination_ is selected as the current address. After pressing `F3` user is prompted for source address:

![memcpy source](img/memcpysrc.png)

selection is confirmed with `GO` key. After that user is prompted for _length_:

![memcpy length](img/memcpylen.png)

selection is again confirmed with `GO` key. Memory is then copied and computer returns to the main screen.

## F4 key - jump to the external ROM

`F4` key allows for quick enter to the external ROM placed at address `0x6000` (external chip select #3). To detect if the external ROM is present monitor checks for a magic value at address `0x6000`. Expected value is `0x4B41` (little-endian). If this check is successful jump to external ROM at address `0x6002` is performed. Otherwise an error message is displayed:

![error](img/f4fail.png)

# License

Free for non-commercial use and educational purposes. See LICENSE.md for details.
