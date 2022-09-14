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


Compiler Interal Workings
Embedded devices require software that circumvent some of the operations the compiler performs automatically.

1. Source code is run through a preprocesser, which handles all the lines that begin with #, called directives.
2. Compiler takes the preprocessed source code and turns it into assembly language code. 
	C code is machine-independent and can be compiled and run on multiple platforms.
	Assembly language is machine-dependent and can run on only one type of platform.
3. Assembly language file is passed through an assembler, that turns it into an object file.
	The object file contains just code. The program needs additional code to work.
4. Linker takes the object code in the object file and combines (links) it with useful code already on the platform.


gcc is designed as a executive program: preprocessor (cpp), C compiler (cc1), assembler (as), linker (ld), etc...

The Preprocessor
1st program ran is the preprocessor - a macro processer - that handles all the lines that begin with #.

output of the preprocessor : gcc -E name.c > hello.i

The Compiler
It turns the C language code into assembly language.

out of the compiler: gcc -S hello.c


The Assembler
Assembly language file goes into the assembler and translated into machine code.
The option -Wa lets us pass flags to the assembler.
Columns:
1st - line number
2nd - address of the data being stored
3rd - numberical values to be stored in memory in hexadecimal format
4th - text of the assembly language code
3rd - assembly language instruction based on push or pop

The Linker
Object file and some of the components of libc need to be combined to make a program.
	The linker takes the files needed to make up the program.
	Combines them,
	Assign real memory addresses to each componenet
The option -Wl lets gcc to pass the option flags.
gcc -Wall -Wextra -static -Wl,-Map=hello.map -o hello hello.o

static - changes the executable from dynamic to statically liked so that memory map behaves like an embedded system
map - maps the memory from which linker placed them.

static and map are used to avoid complexities of dynamic linking.

.o - object file are relocatable.

The linker also goes through the libraries used by the program, extract any needed object files, and
include them in the final program.
