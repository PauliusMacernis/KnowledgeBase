- **What is the difference between `javac` and `java` commands?**  
`javac` command is the command to start the java coompiler (c at the end of the javac). After the compiler creates the byte code you can call the `java` command to start the compiled programm and give it the name of your compiled programm. So `java` command (without a c) starts a Java application. It does this by starting a Java runtime environment, loading a specified class, and calling that class's main method.  
Read more:  
https://teamtreehouse.com/community/difference-between-java-and-javac  

- **What is the differece between Java development kit (JDK) and Java runtime environment (JRE)?**  
JDK contains JRE + development tools.  

- **What is the difference between the Java runtime environment (JRE) and Java virtual machine (JVM)?**  
Java Runtime Environment contains JVM, class libraries, and other supporting files. It does not contain any development tools such as compiler, debugger, etc. Actually JVM runs the program, and it uses the class libraries, and other supporting files provided in JRE.  
JVM contains (class loader & byte code verifier) and the Execution engine (interpreter & JIT). The compiler will convert the source code into intermediate byte codes. Where this byte codes is given to JVM for execution. The class loader in the JVM will load the byte codes and does linking with class libraries provided by the JRE. Then the code will be given to execution engine in the JVM wich interprets the the unrepeated code and compiles the repeated code (for example loops) finally converting into machine code (object code). Then it will give the machine code to the microprocessor for execution.  
Read more:  
https://stackoverflow.com/questions/2812549/what-is-the-difference-between-the-jre-and-jvm  

- 
