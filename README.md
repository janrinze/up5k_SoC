# Simple SoC for ICE40UP5K-B-EVN board

Designed as a demo platform for a small FPGA workshop.

![Image of Upduino V2.0 with SDcard](https://github.com/janrinze/up5k_SoC/blob/SDDOS/2019-04-05.jpg)

## System

	CPU:	16 bit RISC (12Mhz, ~10 MIPS)
	MEM:	64Kx16 SPRAM
	I/O:	1x serial 1000000 8N1 (8 byte input buffer)
		1x serial 1000000 8N1 (debug port)
		16 bit GPIO

## Requirements
* ICE40UP5K-B-EVN board
* installation of icestorm tools from https://github.com/cliffordwolf/icestorm
* 3.3 volt USB to serial cable
* SDcard adapter (like Velleman VMA304)

## Demo binary installation
````
    iceprog binary/BasicDemo.bin
````

## Connecting a 3.3 volt USB to serial on console
````
	black wire connect to gnd
	green wire (serial tx) connect to 6A
	white wire (serial rx) connect to 0A
````

## Connecting a SDcard
````
	black wire to connect gnd SDcard to gnd on Upduino V2.0
	red wire to connect 3.3V SDcard to 3.3V on Upduino V2.0
	MISO SDcard to pin labeled '4' on Upduino V2.0
	MOSI SDcard to pin labeled '3' on Upduino V2.0
	SCK SDcard to pin labeled '48' on Upduino V2.0
	CS SDcard to pin labeled '45' on Upduino V2.0
	
	SDcard format is SDDOS (Acorn Atom simple filing system)
````

## Expected serial console output
````
Simple SoC (Version 0.2)
128KB 16 bit RISC (Version 1.1)
Basic starting at 0x036D to 0x7DC6.
>
````

## Hello World, a test basic program
````
10 PRINT "HELLO WORLD"'
20 GOTO 10
RUN
````
Copy the basic text to the serial console to run the program. Escape will stop the basic program. The basic interpreter is crude and slow so don't expect too much from this demo. Also the expression solver does not do precedence yet be sure to write like A+(B*C) to ensure correctness. The basic interpreter has borrowed a lot of ideas from ATOM Basic. So only A..Z are integer variables. No strings yet although PRINT accepts double quote strings.

## Mount SDcard containing SDDOS image and load a file.
````
Simple SoC (Version 0.2)
128KB 16 bit RISC (Version 1.1)
Basic starting at 0x036D to 0x7DC6.
>SDDOS
SDv2 block addressing
>MOUNT 0,2
>DIR 0
CYLON AT
---------------------------------------
CYLONAT   2900 C2B2 1300 0300 !BOOT    8200 8200 00A2 0200
>LOAD 0,"CYLONAT"
>LIST
1REM CYLON ATTACK
10O=#28F0;M=O+4;DIMT3,A14,H4
... Many more lines..
>
````

## To be released
simpleSoCcompiler (compiles C/C++ like code)

simpleSoClibrary  (easy access to hardware)

## Other
Possible IceStudio blocks for easy quick and dirty implementations.

IceStudio is not yet fully compatible with the UP5K.
