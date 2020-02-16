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

