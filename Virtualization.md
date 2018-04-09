## Virtualization

- What are Virtualization Extensions about? For example: `VT-x` on Intel CPUs, `AMD-V` on AMD CPUs.
<a href="#" title="
">⌘</a>

- What are the differences between VT-x, VT-d, GVT-d -g and -s and IOMMU, and AMD-Vi?
<a href="#" title="
">⌘</a>

- **What is the difference between bytecode of Virtual machine (e.g. Java virtual machine (JVM) of Java, Zend engine of PHP, Common Language Runtime (CLR) of Common Language Infrastructure (CLI) languages like C#, etc.) and machine code?**  
Bytecode is a "temporary code". This "temporary code" is being called `.class` files (or simply Java ARchive (JAR) package containing .class files plus some extra files like text, images, etc.) on JVM, opcodes on Zend engine, CIL code on CLR, etc. A process known as just-in-time compilation converts compiled code into machine instructions which the computer's CPU then executes. 
Ultimately, programs and so bytecode must be translated into instructions that a CPU will understand, and the CPU doesn’t care which programming language you use to produce those instructions. And just like how a CPU doesn’t care which programming language you use to generate machine instructions, the virtual machine doesn’t care how you create bytecode. It doesn’t care if you use Scala, JRuby, Clojure, or even Java to create the bytecode of, for example Java.  
Read more:  
https://www.braveclojure.com/java/  
https://stackoverflow.com/questions/3380581/does-php-have-a-virtual-machine-like-java  
https://en.wikipedia.org/wiki/List_of_CLI_languages  
https://en.wikipedia.org/wiki/Common_Language_Runtime  
https://en.wikipedia.org/wiki/Java_class_file  
https://en.wikipedia.org/wiki/JAR_(file_format)  
http://php.net/manual/en/internals2.opcodes.php  

