# up5k_SoC
Simple SoC for ICE40UP5K-B-EVN board

Designed as a demo platform for a small FPGA workshop.

System :
    CPU: 16 bit RISC (12Mhz, ~10 MIPS)
    MEM: 64Kx16 SPRAM
    I/O: 1x serial 1000000 8N1 (8 byte input buffer)
	 1x serial 1000000 8N1 (debug port)
	 16 bit GPIO

Demo binary:
    iceprog binary/simplesoc.bin
    iceprog -o 320k binary/demo1.bin

To be released:
    simpleSoCcompiler (compiles C/C++ like code)
    simpleSoClibrary  (easy access to hardware)

Other:
    Possible IceStudio blocks for easy quick and dirty implementations.
    IceStudio is not yet fully compatible with the UP5K.
