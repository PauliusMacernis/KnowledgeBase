## General
- What is the difference between a fat client and a thin client (for example: a zero client, a web client, etc.)?
<a href="#" title="
https://en.wikipedia.org/wiki/Thin_client
 ">⌘</a>

- What is the difference between a library and a driver?
<a href="#" title="
Technically, they're the same thing: bodies of subroutines whose names are exported to a linker (static or runtime). By convention, a 'library' is used directly by an application, whose programmer will require documentation and header files. A 'driver', by contrast, is defined by a binary API and is used in some kind of framework, hence printer driver and video driver.
 ">⌘</a>
 
- What is the difference between a `folder` and a `directory` (a `dir`)?
<a href="#" title="
 ">⌘</a>
 
 - What is the difference between arguments and options (programming)?
<a href="#" title="
 ">⌘</a>
 
- What is Semantic Versioning Specification (SemVer)?
<a href="#" title="
More info: http://semver.org/
">⌘</a>

- What is Multipurpose Internet Mail Extensions (MIME)?
<a href="#" title="
More info: https://en.wikipedia.org/wiki/MIME
">⌘</a>

- Why do programmers use `Acme` as a package, namespace or directory name?
<a href="#" title="
More info: https://softwareengineering.stackexchange.com/questions/221953/why-do-programmers-use-acme-as-a-package-namespace-or-directory-name , https://en.wikipedia.org/wiki/Acme_Corporation
">⌘</a>

- What is Read–Eval–Print Loop (REPL)?
<a href="#" title="
More info: https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop
">⌘</a>

- **What is the difference between bytecode of Virtual machine (e.g. Java virtual machine (JVM) of Java, Zend engine of PHP, Common Language Runtime (CLR) of Common Language Infrastructure (CLI) languages like C#, etc.) and machine code?**  
Bytecode is a "temporary code". This "temporary code" is being called `.class` files (or simply Java ARchive (JAR) package containing .class files plus some extra files like text, images, etc.) on JVM, opcodes on Zend engine, CIL code on CLR, etc. A process known as just-in-time compilation converts compiled code into machine instructions which the computer's CPU then executes. 
Ultimately, programs and so bytecode must be translated into instructions that a CPU will understand, and the CPU doesn’t care which programming language you use to produce those instructions.  
Read more:  
https://www.braveclojure.com/java/  
https://stackoverflow.com/questions/3380581/does-php-have-a-virtual-machine-like-java  
https://en.wikipedia.org/wiki/List_of_CLI_languages  
https://en.wikipedia.org/wiki/Common_Language_Runtime  
https://en.wikipedia.org/wiki/Java_class_file  
https://en.wikipedia.org/wiki/JAR_(file_format)  
http://php.net/manual/en/internals2.opcodes.php  
