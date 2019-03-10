### Simple SoC for ICE40UP5K-B-EVN board

Designed as a demo platform for a small FPGA workshop.

# System

	CPU:	16 bit RISC (12Mhz, ~10 MIPS)
	MEM:	64Kx16 SPRAM
	I/O:	1x serial 1000000 8N1 (8 byte input buffer)
		1x serial 1000000 8N1 (debug port)
		16 bit GPIO

# Demo binary installation
````
    iceprog binary/simplesoc.bin
    iceprog -o 320k binary/demo1.bin
````

# Connecting a 3.3 volt USB to serial on console
````
	black wire connect to gnd
	green wire (serial tx) connect to 6A
	white wire (serial rx) connect to 0A
````

# Connecting a 3.3 volt USB to serial on debug port
````
	black wire connect to gnd
	green wire (serial tx) connect to 16A
	white wire (serial rx) connect to 18A
````

# To be released
simpleSoCcompiler (compiles C/C++ like code)

simpleSoClibrary  (easy access to hardware)

# Other
Possible IceStudio blocks for easy quick and dirty implementations.

IceStudio is not yet fully compatible with the UP5K.
