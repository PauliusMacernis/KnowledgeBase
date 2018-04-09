# PHP
- Lets say I make HTTPS request to PRODUCTION server. How can I find the most time-consuming code blocks within the project files I am interested in the most?
<a href="#" title="
">⌘</a>

- What does the "&" mean in a URL?
<a href="#" title="
It separates data into pairs of key and value. Many pairs may exist in one URL.
">⌘</a>

- What does the "+" mean in a URL?
<a href="#" title="
It is encoded space character.
">⌘</a>

- What does the "=" mean in a URL?
<a href="#" title="
 It is separator between key and value in pair of key and value. Within each pair, the key part is on the left of an equal sign (=), while the value is on the right.
">⌘</a>

- What does the "%xx" mean in a URL?
<a href="#" title="
 xx is the hexadecimal version of its ASCII value.
">⌘</a>

- What is the difference between URL and URI?
<a href="#" title="
">⌘</a>

- What is CGI (Common Gateway Interface) in PHP?
<a href="#" title="
CGI is the API (Application Programming Interface) for the web server. CGI is an interface which tells the webserver how to pass data to and from an application. More specifically, it describes how request information is passed in environment variables (such as request type, remote IP address), how the request body is passed in via standard input, and how the response is passed out via standard output. For example, the flow: user (client) request for page --> webserver --[CGI]--> Server side Program --> MySQL Server. Most if not all, webservers can be configured to execute a program as a 'CGI'. This means that the webserver, upon receiving a request, will forward the data to a specific program, setting some environment variables and marshalling the parameters via standard input and standard output so the program can know where and what to look for. The main benefit is that you can run ANY executable code from the web, given that both the webserver and the program know how CGI works. That's why you could write web programs in C or Bash with a regular CGI-enabled webserver. That, and that most programming environments can easily use standard input, standard output and environment variables. Specific for PHP, means of communication between scripts and the webserver most of the time is an embedded interpreter called mod_php. In addition, it is worth to mention that CGI refers to both the protocol and the scripts executed via it. So, PHP can run using CGI or with a special module (mod_php). When running via mod_php is not CGI at all (even if based on it). It is also possible to use PHP as daemon and skip the whole CGI step. Then all what is needed is an HTTP parser, or just proxy through NGINX. More info:--'www.whizkidtech.redprince.net/cgi-bin/tutorial'--AND--'stackoverflow.com/questions/2089271/what-is-common-gateway-interface-cgi'--AND--'www.ietf.org/rfc/rfc3875.txt'
">⌘</a>

- What is `cgi-bin` directory found on some web servers for?
<a href="#" title="
That is the traditional place for cgi programs, many webservers come with this directory pre configured to execute all binaries there as CGI programs.
">⌘</a>

- What are `*.cgi` files inside of `cgi-bin` directory about?
<a href="#" title="
The .cgi extension denotes an executable that is expected to work through the CGI. Many webservers come with cgi-bin directory pre configured to execute all binaries there as CGI programs.
">⌘</a>

- Explain how a C program (or any other program compiled for the web server system) can be run by using CGI.
<a href="#" title="
You compile the executable once, the webserver executes the program (usually the program is in cgi-bin directory) and passes the data in the request to the program and outputs the received response. CGI specifies that one program instance will be launched per each request. This is why CGI is inefficient and kind of obsolete nowadays. Back then URLs typically mapped to scripts: foo.com/cgi-bin/date.cgi?date=1992-02-02 Nowadays that no longer happens, but it's irrelevant, the URL mapping for CGI scripts must still happen, if it's not direct, it's in the server's configuration (this url (foo.com/date/1992/02/02) maps to the url containing the path to the CGI script (foo.com/cgi-bin/date.cgi?date=1992-02-02) In Apache you do that with mod_rewrite, typically.) In any case, it's a separate problem. Webservers do not compile code. And the CGI spec keeps us from having to link against the webserver.
">⌘</a>

- What is the difference between CGI and FastCGI?
<a href="#" title="
CGI specifies that one program instance will be launched per each request. This is why CGI is inefficient and kind of obsolete nowadays. However, CGI is still used when performance is not paramount and a simple means of executing code is required. There are more modern means of executing any program in a web enviroment. Currently the most famous is FastCGI. ...
">⌘</a>

- What is ZTS (Zend Thread Safety) in PHP?
<a href="#" title="
http://stackoverflow.com/questions/681081/is-php-thread-safe , https://gist.github.com/tegansnyder/ad32f2068e7e30d2692c06df32314ed4 , http://flylib.com/books/en/2.565.1.14/1/ , 
">⌘</a>

- What do "thread safe" and "non-thread safe" mean in PHP?
<a href="#" title="
">⌘</a>

- What is PHP Data Objects (PDO)?
<a href="#" title="
PDO is abstraction layer (interface) for database extensions (drivers, libraries, etc.). The PHP Data Objects (PDO) extension defines a lightweight, consistent interface for accessing databases in PHP. Each database driver that implements the PDO interface can expose database-specific features as regular extension functions. Note that you cannot perform any database functions using the PDO extension by itself; you must use a database-specific PDO driver to access a database server.
PDO provides a data-access abstraction layer, which means that, regardless of which database you're using, you use the same functions to issue queries and fetch data. PDO does not provide a database abstraction; it doesn't rewrite SQL or emulate missing features. You should use a full-blown abstraction layer if you need that facility.
PDO ships with PHP 5.1, and is available as a PECL extension for PHP 5.0; PDO requires the new OO features in the core of PHP 5, and so will not run with earlier versions of PHP.
">⌘</a>

- Are PHP function names case sensitive?
<a href="#" title="
PHP function names are case-insensitive. http://php.net/manual/en/functions.user-defined.php
">⌘</a>

- What is the difference between "static::" and "self::" when using to reference a constant or static variable within a class?
<a href="#" title="
self:: is not inheritance-aware where static:: is (in PHP). When it comes to defining a bunch of constants within a class, if you want to override those constants in a subclass to change default ~behaviours~, it becomes necessary to use static:: so that a method on the parent class that references the constant, honours the ~override~. More info: https://stackoverflow.com/questions/13613594/overriding-class-constants-vs-properties
">⌘</a>

- What is the difference between "static::" and "$this::" when using to reference a constant or static variable within a class?
<a href="#" title="
It works the same (?). More info: https://stackoverflow.com/questions/13613594/overriding-class-constants-vs-properties
">⌘</a>

- What is the difference between serialization (e.g. serialize PHP function) and json encoding (e.g. json_encode PHP function)?
<a href="#" title="
...
">⌘</a>

- May class constructors, destructors, clone methods declare return types on `PHP7`?
<a href="#" title="
Class constructors, destructors and clone methods may not declare return types (fatal error will rise if given). All other methods may have return types. All of this applies for PHP 7.0 and above. More info: https://wiki.php.net/rfc/return_types
">⌘</a>

- What is PHPCR (PHP Content Repository)?
<a href="#" title="
http://phpcr.github.io/about/
">⌘</a>

- **What are options for PHP virtual machine?**  
  - Zend engine ( http://www.zend.com/products/zend_engine/in_depth , https://en.wikipedia.org/wiki/Zend_Engine ) - comes by default
  - Facebook’s HipHop virtual machine (HHVM) ( https://hhvm.com/ )  
  HipHop takes normal PHP code and transforms it into C++, which is then compiled in machine code.  
  - IBM’s WebSphere sMash ( https://www.ibm.com/developerworks/websphere/library/techarticles/0809_phillips/0809_phillips.html )  WebSphere sMash is a Java implementation of a PHP runtime environment. The PHP code is compiled into Java bytecode which runs on the Java Virtual Machine.  
  - Caucho’s Quercus ( http://quercus.caucho.com/ )  
  Quercus is another Java implementation of a PHP runtime environment. 
  - Phalanger ( https://github.com/DEVSENSE/Phalanger )  
  Phalanger is a strange creature. It is sort of like PHP.NET. It takes your normal PHP code and compiles it into MSIL, which can then be run by .NET or Mono. The major advantage to using Phalanger is that it makes it possible to access .NET classes in PHP (for example, VB.NET or C#).  
  Read more:  
  https://www.jacoballred.com/web-dev/zend-alternatives/  
  
- **What is `phpng`?**  
Phpng is the codename for PHP virtual machine - Zend Engine III. 

- **What is Zend engine used for?**  
Zend Engine is used internally by PHP as a compiler and runtime engine (aka. virtual machine of PHP). PHP Scripts are loaded into memory and compiled into Zend opcodes. These opcodes are executed and the HTML generated is sent to the client.  
To implement a Web script interpreter, three parts are needed: 1) The interpreter part analyzes the input code, translates it, and executes it. 2) The functionality part implements the functionality of the language (its functions, etc.). 3) The interface part talks to the Web server, etc.  
Zend takes part 1 completely and a bit of part 2; PHP takes parts 2 and 3.  
Read more:  
https://en.wikipedia.org/wiki/Zend_Engine  
https://en.wikipedia.org/wiki/PHP#NG  






