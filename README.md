# bare_metal_C
This is repository is about embedded programming. This will 
help with programming an embedded system. This is written in 
C because of precise control over what a program does. C is 
used to program a low-end system on a chip (SOC) based on the 
STM32F030x4 processor.

32-bit integers are more efficient and faster because 32 bits 
is the natural number size for the ARM. IF 16-bit arithmetic 
is used, it does 32-bit calculations and then throws away 16 
bits.

This project uses the STMicroelectronics NUCLEO-F030R8

Compiler Flags
	-ggdb Complies the program so we can debug it. It adds debugging information to the output file that allows the debugger 
to understand what is going on

	-Wall Turns on a set of warnings that will flag correct but questionaable code.

	-Wextra Turns on extra warnings in an effort to make our code more precise.

	-o name Puts the output of our program in the file name.
