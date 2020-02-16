# x86-64 Assembly Language Programming with Ubuntu by Ed Jorgensen, Ph.D. ; Version 1.1.40; January 2020

http://www.egr.unlv.edu/~ed/assembly64.pdf

## Chapter 1

Assembly language is as close to the processor as you can get as a programmer. Programs written in a high-level language are translated into assembly language in order for the processor to execute the program. The highlevel language is an abstraction between the language and the actual processor instructions. As such, the idea that “assembly is dead” is nonsense.  

The reasons for learning assembly language are more about understanding how a computer works instead of developing large programs.  

Since assembly language is machine specific, the lack of portability is very limiting for programming projects.  

In the long run, learning the underlying principles, including assembly language, is what makes the difference between a coding technician unable to cope with changing languages and a computer scientist who is able to adapt to the ever-changing technologies.  

...knowing the capabilities of assembly language provides useful insights into what is possible, what is easy, and what might be more difficult or slower.  

Additionally, use of the stack and the associated call frame is the basis for recursion and understanding the fairly straightforward implementation of recursive functions.  

Working at the assembly language level and performing some low-level input/output operations provides a more detailed understanding of how input/output and buffering really works. This includes the differences between interactive input/output, file input/output, and the associated operating system services.  

Ubuntu docs: https://help.ubuntu.com/community/CommunityHelpWiki  

Bash docs: http://linuxcommand.org/index.php  

Architecture references:  

- https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-software-developer-vol-1-manual.pdf  
- https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-software-developer-instruction-set-reference-manual-325383.pdf  
- https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-software-developer-system-programming-manual-325384.pdf  

YASM References:  

- Website: http://yasm.tortall.net/  
- Documentation: http://yasm.tortall.net/Guide.html  

DDD Debugger References:  

- Website: http://www.gnu.org/software/ddd/  
- Documentaton: http://www.gnu.org/software/ddd/manual/  

## Chapter 2

The basic components of a computer include a Central Processing Unit (CPU), Primary Storage or Random Access Memory (RAM), Secondary Storage, Input/Output devices (e.g., screen, keyboard, mouse), and an interconnection referred to as the Bus.  
The architecture is typically referred to as the Von Neumann Architecture, or the Princeton architecture.  

The CPU executes the program from primary storage or RAM.  

Primary storage or main memory is also referred to as **volatile memory** since when power is removed, the information is not retained and thus lost. Secondary storage is referred to as **non-volatile memory** since the information is retained when powered off.  

For example, C/C++ declarations are mapped as follows:  

| C/C++ Declaration | Storage     | Size (bits) | Size (bytes) |
|-------------------|-------------|-------------|--------------|
| char              | Byte        | 8-bits      | 1 byte       |
| short             | Word        | 16-bits     | 2 bytes      |
| int               | Double-word | 32-bits     | 4 bytes      |
| unsigned int      | Double-word | 32-bits     | 4 bytes      |
| long              | Quadword    | 64-bits     | 8 bytes      |
| long long         | Quadword    | 64-bits     | 8 bytes      |
| char *            | Quadword    | 64-bits     | 8 bytes      |
| int *             | Quadword    | 64-bits     | 8 bytes      |
| float             | Double-word | 32-bits     | 4 bytes      |
| double            | Quadword    | 64-bits     | 8 bytes      |

*The asterisk indicates an address variable. For example, int * means the address of
an integer. Other high-level languages typically have similar mappings.*  
*Note, the 'long' type declaration is compiler dependent. Type shown is for gcc and g++ compilers.*  

For more information, refer to:  

- http://en.wikipedia.org/wiki/Central_processing_unit
- http://en.wikipedia.org/wiki/Die_(integrated_circuit)
- http://en.wikipedia.org/wiki/Arithmetic_logic_unit
- http://en.wikipedia.org/wiki/Processor_register
- http://en.wikipedia.org/wiki/Cache_(computing)

There are sixteen, 64-bit General Purpose Registers (GPRs). The GPRs are described in
the following table. A GPR register can be accessed with all 64-bits or some portion or
subset accessed.  

| 64-bit register | Lowest 32-bits | Lowest 16-bits | Lowest 8-bits |
|-----------------|----------------|----------------|---------------|
| rax             | eax            | ax             | al            |
| rbx             | ebx            | bx             | bl            |
| rcx             | ecx            | cx             | cl            |
| rdx             | edx            | dx             | dl            |
| rsi             | esi            | si             | sil           |
| rdi             | edi            | di             | dil           |
| rbp             | ebp            | bp             | bpl           |
| rsp             | esp            | sp             | spl           |
| r8              | r8d            | r8w            | r8b           |
| r9              | r9d            | r9w            | r9b           |
| r10             | r10d           | r10w           | r10b          |
| r11             | r11d           | r11w           | r11b          |
| r12             | r12d           | r12w           | r12b          |
| r13             | r13d           | r13w           | r13b          |
| r14             | r14d           | r14w           | r14b          |
| r15             | r15d           | r15w           | r15b          |

Additionally, some of the GPR registers are used for dedicated purposes as described in the later sections.  

When using data element sizes less than 64-bits (i.e., 32-bit, 16-bit, or 8-bit), the lower portion of the register can be accessed by using a different register name as shown in the table.  

The first four registers, rax, rbx, rcx, and rdx also allow the bits 8-15 to be accessed with the ah, bh, ch, and dh register names. With the exception of ah, these are provided for legacy support and will not be used in this text.  

The ability to access portions of the register means that, if the quadword rax register is set to 50,000,000,000 (fifty billion, 10-based system), the rax register would contain the following value in hex.  

`rax = 0000 000B A43B 7400`  

If a subsequent operation sets the word ax register to 50,000 (fifty thousand, 10-based system, which is C35016), the rax register would contain the following value in hex  

`rax = 0000 000B A43B C350`  

In this case, when the lower 16-bit ax portion of the 64-bit rax register is set, the upper 48-bits are unaffected.  

If a subsequent operation sets the byte sized al register to 50 (fifty, 10-based system, which is 32 in HEX), the
rax register would contain the following value in hex.  

`rax = 0000 000B A43B C332`  

When the lower 8-bit al portion of the 64-bit rax register is set, the upper 56-bits are unaffected.  

For 32-bit register operations, the upper 32-bits is cleared (set to zero). Generally, this is not an issue since operations on 32-bit registers do not use the upper 32-bits of the register. For unsigned values, this can be useful to convert from 32-bits to 64-bits. However, this will not work for signed conversions from 32-bit to 64-bit values. Specifically, it will potentially provide incorrect results for negative values.  

(The following image that relates to the same topic is taken from https://youtu.be/BWRR3Hecjao?t=188 )
![https://youtu.be/BWRR3Hecjao?t=188]https://github.com/sugalvojau/Knowledge-base/blob/master/Summaries/Assembly/Screenshot%20from%202020-02-17%2000-04-57.png?raw=true
