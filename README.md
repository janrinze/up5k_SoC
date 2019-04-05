# Simple SoC for ICE40UP5K-B-EVN board

Designed as a demo platform for a small FPGA workshop.
![Image of Upduino V2.0 with SDcard]
(https://github.com/janrinze/up5k_SoC/SDDOS/2019-04-05.jpg)
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

## Connecting a 3.3 volt USB to serial on debug port
````
	black wire connect to gnd
	green wire (serial tx) connect to 16A
	white wire (serial rx) connect to 18A
````

## Expected serial console output
````
Simple SoC
128KB
Basic starting at 0x003C to 0x7DC6.
>
````

## Blinkie, a test basic program
````
10 A=#B002
20 POKE A,-1
30 A=#B003
40 V=0;D=0;E=1
50 FOR T=0 TO 5
60 POKE A,D
70 FOR W=0 TO 16
80 IF V=W POKE A,E
90 NEXT
100 NEXT
110 IF V<1 S=1
120 IF V>15 S=-1
130 V=V+S
140 GOTO 50
RUN
````
Copy the basic text to the serial console to run the program. Escape will stop the basic program. The basic interpreter is crude and slow so don't expect too much from this demo. Also the expression solver does not do precedence yet be sure to write like A+(B*C) to ensure correctness. The basic interpreter has borrowed a lot of ideas from ATOM Basic. So only A..Z are integer variables. No strings yet although PRINT accepts double quote strings.

## To be released
simpleSoCcompiler (compiles C/C++ like code)

simpleSoClibrary  (easy access to hardware)

## Other
Possible IceStudio blocks for easy quick and dirty implementations.

IceStudio is not yet fully compatible with the UP5K.
