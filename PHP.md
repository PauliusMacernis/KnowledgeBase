Resources:  
https://www.scalingphpbook.com/  


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

- **What does `php --ini` command do?**  
At first, PHP will load all files in `/etc/php.d/*.ini` as configuration files.  
Then, within each directory, PHP will scan all files ending in `.ini` in alphabetical order.  
A list of the files that were loaded, and in what order, is available by calling `php_ini_scanned_files()`, or by running PHP with the `--ini` option.  
Read more: http://php.net/manual/en/configuration.file.php  

- **What is PHP OPcache?**  
OPcache improves PHP performance by storing precompiled script bytecode in shared memory, thereby removing the need for PHP to load and parse scripts on each request.  
Read more:  
http://php.net/manual/en/book.opcache.php  

- **Explain `php -m | grep opcache`**  
It is a PHP utility (CLI) that shows compiled in PHP modules (`-m`) and sends the list (text) to the `grep` utility. `grep`, which stands for "global regular expression print," processes text line by line and prints any lines which match a specified pattern (`opcache`). It is actually being used for finding if any PHP module matching the string `opcache` exist.  
Read more:  
http://php.net/manual/en/features.commandline.options.php  
http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_02.html  

- **Explain `php -i | grep ^extension_dir`**  
It is a PHP utility (CLI) that shows PHP information (`-i`) and sends the list (text) to the `grep` utility. `grep`, which stands for "global regular expression print," processes text line by line and prints any lines which match a specified pattern (`^extension_dir`). It is actually being used for finding the extensions dir for PHP. "Extensions" - dynamically loadable extensions to load when PHP starts up.  
Read more:  
http://php.net/manual/en/features.commandline.options.php  
http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_02.html  
http://php.net/manual/en/ini.core.php#ini.extension-dir  

- **What is the environment variable `PHP_INI_SCAN_DIR` for?**  
The `PHP_INI_SCAN_DIR` environment variable can be set to override the scan directory of PHP settings (`*.ini` files) set via the configure script. Available since PHP 5.2.0.  
Read more:  
http://php.net/manual/en/configuration.file.php  

- **What is Suhosin?**  
Suhosin (pronounced 'su-ho-shin') is an advanced protection system for PHP installations. It was designed to protect servers and users from known and unknown flaws in PHP applications and the PHP core. Suhosin comes in two independent parts, that can be used separately or in combination. The first part is a small patch against the PHP core, that implements a few low-level protections against buffer overflows or format string vulnerabilities and the second part is a powerful PHP extension that implements numerous other protections.  
Read more:  
https://suhosin.org/stories/index.html  
https://raw.githubusercontent.com/sektioneins/suhosin/master/Changelog  

- **What is Server Application Programming Interface (SAPI)?**  
In computing, Server Application Programming Interface (SAPI) is the direct module interface to web servers such as the Apache HTTP Server, Microsoft IIS, and Oracle iPlanet Web Server. In other words, SAPI is an application programming interface (API) provided by the web server to help other developers in extending the web server capabilities.  
Read more:  
https://en.wikipedia.org/wiki/Server_Application_Programming_Interface  

- **What is the difference between Application Programming Interface (SAPI), Internet Server Application Programming Interface (ISAPI), Netscape Server Application Programming Interface (NSAPI)?**  
Microsoft uses the term Internet Server Application Programming Interface (***ISAPI***), and the defunct Netscape web server used the term Netscape Server Application Programming Interface (***NSAPI***) for the same purpose.  
Read more:  
https://en.wikipedia.org/wiki/Server_Application_Programming_Interface

- **What versions of SAPI PHP has?**  
PHP has a direct module interface called SAPI for different web servers; in the case of PHP 5 and Apache 2.0 on Windows, it is provided in the form of a DLL file called php5apache2.dll, which is a module that, among other functions, provides an interface between PHP and the web server, implemented in a form that the server understands. This form is what is known as a SAPI.  
Different kinds of SAPIs exist for various web-server extensions. For example, in addition to those listed above, other SAPIs for the PHP language include the ***Common Gateway Interface (CGI)*** and ***command-line interface (CLI)*** .  
What about`APache eXtenSion tool` (`apxs`)? `apxs` is a tool for building and installing extension modules for the Apache HyperText Transfer Protocol (HTTP) server. This is achieved by building a dynamic shared object (DSO) from one or more source or object files which then can be loaded into the Apache server under runtime via the LoadModule directive from mod_so.  
Read more:  
https://en.wikipedia.org/wiki/Server_Application_Programming_Interface  
https://httpd.apache.org/docs/current/programs/apxs.html  

- **What is the result of `var_dump(1 <= 0 == 0);`?**  
true  
Read more:  
https://www.php.net/manual/en/language.operators.precedence.php  

- **What are Name resolution rules in PHP?**  
Read more:  
http://php.net/manual/en/language.namespaces.rules.php  

- **How do PEAR, PEAR2, GitHub, Packagist, Pyrus, Composer relate with each other?**  
(The ansswer is the ~article I was about to write in 2014. You may find several errors in the answer so pay attention to what you read. This is simply copy>paste from the archives of mine of 2014. So lets dive into it...)  

***At first, there are major places where projects of PHP reside. Such places are:***  
PEAR ([http://pear.php.net/][1]) - part of PHP,  
PEAR2 ([http://pear2.php.net/][2]) - part of PHP,  
GitHub ([https://github.com/][3]) - not part of PHP.  
Packagist ([https://packagist.org/][4]) - not part of PHP  

***Then, there are manual ways to include the project into the newly building local application. Such ways are:***  
PEAR: Download the source (as zip, tgz, etc.) by using web browser, manually include it to the own project (for example, via "require_once('path to the main file of the downloaded project')", manually add dependencies (other projects related to) and the downloaded project will start working as part of own application.  
  
PEAR2: The same way as PEAR. I am actually not so sure about downloading project files from PEAR2 website, but it seems it is possible. It seems not so easy as to download from PEAR website, but downloading from PEAR2 website is also possible as we can browse inside of PEAR2 project files, so we can download them. Am I right? This is not the recommended way (as I understand it) to download code, but I would like to say that in case of emergency downloading code from PEAR2 website is possible...  
  
GitHub: The same way as PEAR.  
  
Packagist: You cannot download packages from Packagist by using web browser.  

***Then, there are (semi-)automatic ways to include the project into the newly building application. Such ways are:***  
PEAR: uses PEAR (the same name as repository!) package manager to download and install project files. PEAR package manager downloads project files into directory we set in configuration of PEAR package manager. Such directory for downloads are usually set as one of include_path's in PHP configuration, so we have to write shorter path to include the downloaded project files into our own project.  
  
PEAR2: the package manager is called Pyrus. Works almost the same as PEAR package manager, just more flexible. As I understand, the best part of Pyrus is that it allows to have Pyrus installed on the project (local) rather than on the machine (system) only. The PEAR was one per machine (one PEAR per one PHP interpreter to be exact) which means that all projects were having the same installation set of PEAR projects. PEAR was not good in case we had a need for two different sets of PEAR projects (or two different versions of the same project?) on the one and the same machine.  
  
GitHub: uses Git. Git works on OS level.  
  
Packagist: uses Composer. Composer works on project level.  
  
***Whatever we decide to use (PEAR, Pyrus, Git or Composer) we must get those managers from somewhere, properly install. Because there are none of them at our systems usually.***  
PEAR: You get the PEAR installer at first. Then You use PEAR installer to install PEAR package manager. It is confusing (I think so), but it is like it is.. So, You get PEAR installer from here:  
[http://pear.php.net/go-pear][5]  
You download this go-pear script file and run it with PHP. The script file will then install PEAR package manager. After that You will have to make some modifications on Your system to have fully working PEAR packet manager (for example, You would need to add instructions on where to download packages and so on).  
  
Pyrus: there is no such installer for Pyrus as it was for PEAR. Just download the file from here:
[http://pear2.php.net/pyrus.phar][6]  
The file pyrus.phar is the package manager.  
  
Git: download the version which suits Your OS: [http://git-scm.com/downloads][7].  
  
Composer: download the installer from here:  
[https://getcomposer.org/installer][8]  
Run the installer by using PHP and the Composer will be installed. More instructions on how to download could be found here:
[https://getcomposer.org/download/][9]  
  
***Dependency management***  
Some projects depends on others. For example, PEAR project "words_numbers" includes PEAR project "Math_BigInteger" to itself. The "word_numbers" would not work without "Math_BigInteger". The problem here is that both projects are separate and separately changes their own versions in time. The project which includes another project must know which exact version of all available to use.  
  
PEAR: downloading via PEAR package manager (not manually via web browser!) will solve problems associated with dependencies - dependencies will be automatically downloaded together with the project You download. Please let me know if I am wrong here, but it seems to me that few versions of the same project cannot be installed via PEAR. I mean, You cannot install version X of the PEAR project as just to use and then install Y version of the same PEAR project as of dependency case. It will not work, right? There will be some kind of conflict, right?  
  
Pyrus: no problems with dependencies. Pyrus, as in PEAR case, will automatically download required dependencies. It means that You may get few PEAR2 projects instead of one just because of existing dependencies. The same PEAR question applies to Pyrus (can few versions of the same PEAR2 project could be used on one local environment?).  
  
Git: I would say that git does not support such thing as dependency management.  
  
Composer: manages dependencies on the project basis. You make the file (composer.json) in which You describe Your project dependencies and composer will automatically download projects Your project depends on. Each downloadable project may have own dependencies, so Composer will download them as well. Few versions of the same project are allowed.  
Composer: download the installer from here:  
[https://getcomposer.org/installer][10]  
Run the installer by using PHP and the composer will be installed.  
Composer is used per project basis, so it is not kind of PEAR (used per machine). Pyrus and Composer have some similarities and differences as managers, but this is already described here:  
[http://stackoverflow.com/questions/15087502/what-is-the-difference-between-pyrus-and-composer][11]  
  
***Few more things to mention:***  
  
PEAR: You can use PEAR manager to download packages from PEAR only.  
  
Pyrus: You can use Pyrus to download packages from PEAR2 only.  
  
Git: You can use git to get packages from any git repository available to You (GitHub is one of many choices).  
  
Composer: You can use Composer to download packages from Packagist only.  
  
***P.s.***  
It would be nice to include info on PECL somewhere above as I think it must be served in the same plate...  
  [1]: http://pear.php.net/  
  [2]: http://pear2.php.net/  
  [3]: https://github.com/  
  [4]: https://packagist.org/  
  [5]: http://pear.php.net/go-pear  
  [6]: http://pear2.php.net/pyrus.phar  
  [7]: http://git-scm.com/downloads  
  [8]: https://getcomposer.org/installer  
  [9]: https://getcomposer.org/download/  
  [10]: https://getcomposer.org/installer  
  [11]: http://stackoverflow.com/questions/15087502/what-is-the-difference-between-pyrus-and-composer  
