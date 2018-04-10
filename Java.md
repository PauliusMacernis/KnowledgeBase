- **What is the difference between `javac` and `java` commands?**  
`javac` command is the command to start the java coompiler (c at the end of the javac). After the compiler creates the byte code you can call the `java` command to start the compiled programm and give it the name of your compiled programm. So `java` command (without a c) starts a Java application. It does this by starting a Java runtime environment, loading a specified class, and calling that class's main method.  
Read more:  
https://teamtreehouse.com/community/difference-between-java-and-javac  

- **What is the difference between Oracle JDK and Open JDK?**  
Both openjdk and oracle jdk are created and maintained currently by Oracle only.  
openjdk and oracle jdk are implementations of same Java specification passed the TCK(Java Technology Certification Kit).  
The openjdk project is mostly based on hotspot source code donated by Sun. Most of the vendors of JDK are written on top of openjdk by doing few tweaks to \[Mostly to replace licensed proprietary parts / replace with more performant items that only work on specific OS] components without breaking the TCK compatibility.  
Many vendors implemented Java specification and got TCK passed. For example IBM J9 , Azul Zulu , Azul Zing , Oracle JDK.  
Almost every existing JDK is derived from openjdk.  
As suggested by many, licensing is a change between JDK's.  
The build process for Oracle JDK releases builds on OpenJDK 7 by adding just a couple of pieces, like the deployment code, which includes Oracle's implementation of the Java Plugin and Java WebStart, as well as some closed source third party components like a graphics rasterizer, some open source third party components, like Rhino, and a few bits and pieces here and there, like additional documentation or third party fonts. Moving forward, Oracle's intent is to open source all pieces of the Oracle JDK except those that Oracle consider commercial features such as JRockit Mission Control (not yet available in Oracle JDK), and replace encumbered third party components with open source alternatives to achieve closer parity between the code bases. 
Read more:  
https://stackoverflow.com/questions/22358071/differences-between-oracle-jdk-and-open-jdk  
https://en.wikipedia.org/wiki/List_of_Java_virtual_machines#Proprietary_implementations  


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
Read more:  
https://www.braveclojure.com/java/  

- **What is `package`? For example, `package com.shapemaster`.**  
Packages (similar to Clojure’s or PHP's namespaces) provide code organization. Packages contain classes, and package names correspond to filesystem directories. If a file has the line `package com.shapemaster` in it, the directory `com/shapemaster` must exist somewhere on your classpath. Within that directory will be files defining classes.  
Read more:  
https://www.braveclojure.com/java/  

- **What is `import`? For example, `import com.shapemaster.Square;` or `import com.shapemaster.*;`.**  
Java allows us to import classes, which basically means that we can refer to them without using their namespace prefix. So if we have a class in `com.shapemaster` named `Square`, we could write `import com.shapemaster.Square;` or `import com.shapemaster.*;` at the top of a `.java` file to use `Square` in our code instead of `com.shapemaster.Square`.  
Read more:  
https://www.braveclojure.com/java/  

- **What does `jar cvfe conversation.jar PirateConversation PirateConversation.class pirate_phrases/*.class` do?**  
We bundle all the class files into `conversation.jar`. Using the `e` flag, we also indicate that the `PirateConversation` class is the entry point. The entry point is the class that contains the `main` method that should be executed when the JAR as a whole runs, and jar stores this information in the file `META-INF/MANIFEST.MF` within the JAR file. If we were to read that file, it would contain this line: `Main-Class: PirateConversation`.  
Read more:  
https://www.braveclojure.com/java/  

- **What is JAR (Java ARchive) file for?**  
A JAR (Java ARchive) is a package file format typically used to aggregate many Java class files and associated metadata and resources (text, images, etc.) into one file for distribution.  
JAR files are archive files that include a Java-specific manifest file. They are built on the ZIP format and typically have a `.jar` file extension.  
The contents of a JAR file may be extracted using any standard decompression software, or the jar command line utility: `jar -xf foo.jar`.  
Developers can digitally sign JAR files. In that case, the signature information becomes part of the embedded manifest file. The JAR itself is not signed, but instead every file inside the archive is listed along with its checksum; it is these checksums that are signed. Multiple entities may sign the JAR file, changing the JAR file itself with each signing, although the signed files themselves remain valid.  
The typical invocation is `java -jar foo.jar` from a command line.  
Native launchers can be created on most platforms. For instance, Microsoft Windows users who prefer having Windows EXE files can use tools such as JSmooth, Launch4J, WinRun4J or Nullsoft Scriptable Install System to wrap single JAR files into executables.  
Read more:  
https://en.wikipedia.org/wiki/JAR_(file_format)  

- **What is JAR (Java ARchive) manifest file (`META-INF/MANIFEST.MF`) for?**  
A manifest file is a metadata file contained within a JAR. It defines extension and package-related data. It contains name-value pairs organized in sections. If a JAR file is intended to be used as an executable file, the manifest file specifies the main class of the application. The manifest file is named `MANIFEST.MF`. The manifest directory has to be the first entry of the compressed archive. The manifest appears at the canonical location `META-INF/MANIFEST.MF`. There can be only one manifest file in an archive and it must be at that location.  
Manifest file may be used for: Package Sealing (all classes defined in the chosen package are archived in the same JAR file), Package Versioning (several manifest headers hold versioning information, one set of headers can be assigned to each package), Dependencies (to specify all the classes that must be loaded for an application to be able to run), etc.  
Read more: https://en.wikipedia.org/wiki/JAR_(file_format)  





