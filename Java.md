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

- **What does `java -classpath /tmp` do?**  
When we run `java PiratePhrases`, the JVM first looks at a classpath for a class named PiratePhrases (`PiratePhrases.class`). The classpath is the list of filesystem paths that the JVM searches to find a file that defines a class. By default, the classpath includes the directory we’re in when we run java. Try running `java -classpath /tmp PiratePhrases` and you’ll get an error, even though `PiratePhrases.class` is right there in the current directory.  
In Java, we’re allowed only one public class per file, and the filename must match the class name. This is how `java` knows to try looking in `PiratePhrases.class` for the `PiratePhrases` class’s bytecode. After `java` found the bytecode for the `PiratePhrases` class, it executed that class’s `main` method. Java’s similar to C in that whenever you say “run something, and use this class as your entry point,” it will always run that class’s `main` method; therefore, that method must be `public`.  


