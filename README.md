# Questions
There are some questions that needs to be answered by every senior web developer anytime. 


## General
- What is the difference between a library and a driver?
<a href="#" title="
Technically, they're the same thing: bodies of subroutines whose names are exported to a linker (static or runtime). By convention, a 'library' is used directly by an application, whose programmer will require documentation and header files. A 'driver', by contrast, is defined by a binary API and is used in some kind of framework, hence printer driver and video driver.
 ">⌘</a>
 
- What is Semantic Versioning Specification (SemVer)?
<a href="#" title="
More info: http://semver.org/
">⌘</a>


## Licenses
- ...


## Organizations
- What is SAP SE (Systeme, Anwendungen und Produkte in der Datenverarbeitung; "Systems, Applications & Products in Data Processing"), or just 'SAP'?
<a href="#" title="
SAP SE (/ɛseɪˈpi/) (Systeme, Anwendungen und Produkte in der Datenverarbeitung; 'Systems, Applications & Products in Data Processing') is a European multinational software corporation that makes enterprise software to manage business operations and customer relations. SAP is headquartered in Walldorf, Baden-Württemberg, with regional offices in 130 countries. The company has over 335,000 customers in 190 countries. The company is a component of the Euro Stoxx 50 stock market index. Founded in Weinheim, Germany (1972; 45 years ago). As of 2016, SAP is the world's third largest software and programming company. Notable products: 1) SAP ASE (Adaptive Server Enterprise), originally known as Sybase SQL Server, and also commonly known as Sybase DB or ASE, is a relational model database server product for businesses developed by Sybase Corporation which became part of SAP SE. 2) other
 ">⌘</a>
 

### Encodings
- What is Unicode?
<a href="#" title="
Unicode is a computing industry standard for the consistent encoding, representation, and handling of text expressed in most of the world's writing systems. Developed in conjunction with the Universal Coded Character Set (UCS) standard and published as The Unicode Standard. The standard consists of a set of code charts for visual reference, an encoding method and set of standard character encodings, a set of reference data files, and a number of related items, such as character properties, rules for normalization, decomposition, collation, rendering, and bidirectional display order (for the correct display of text containing both right-to-left scripts, such as Arabic and Hebrew, and left-to-right scripts). Unicode can be implemented by different character encodings. The most commonly used encodings are UTF-8, UTF-16 and the now-obsolete UCS-2. We often say 'Unicode' when we mean 'not ASCII', but that’s silly since of course all of ASCII is also included in Unicode.
">⌘</a>
 
- What is Unicode Consortium?
<a href="#" title="
The Unicode Consortium (Unicode Inc.) is a 501(c)(3) type non-profit organization that coordinates the development of the Unicode standard. Its stated goal is to eventually replace existing character encoding schemes with Unicode and its standard Unicode Transformation Format (UTF) schemes, contending that many of the alternative schemes are limited in size and scope, and are incompatible with multilingual environments. Tho Organization cooperates with many standards development organizations, including ISO/IEC JTC1, W3C, IETF, and ECMA. Full members include most of the main computer software and hardware companies with any interest in text-processing standards, including Adobe Systems, Apple, Facebook, Google, Huawei, IBM, Microsoft, Oracle Corporation, Yahoo! and SAP SE.
">⌘</a>
 
- What is American Standard Code for Information Interchange (ASCII)?
<a href="#" title="
ASCII, sometimes called US-ASCII, is a character encoding standard. ASCII codes represent text in computers, telecommunications equipment, and other devices. Most modern character-encoding schemes are based on ASCII, although they support many additional characters. ASCII originally based on the English alphabet, ASCII encodes 128 specified characters into seven-bit integers. The characters encoded are numbers 0 to 9, lowercase letters a to z, uppercase letters A to Z, basic punctuation symbols, control codes that originated with Teletype machines, and a space. ASCII includes definitions for 128 characters: 33 are non-printing control characters (many now obsolete) that affect how text and space are processed and 95 printable characters, including the space (which is considered an invisible graphic).
">⌘</a>
 
- What is the difference between ASCII and US-ASCII?
<a href="#" title="
No real difference, both are about the same. However, Internet Assigned Numbers Authority (IANA) encourages use of the name 'US-ASCII' for Internet uses of ASCII (even if it is a redundant acronym, but the US is needed because of regular confusion of the ASCII term with other 8 bit based character encoding schemes such as Extended ASCII or UTF-8 for example).
">⌘</a>
 
- What is the difference between ASCII and Extended ASCII?
<a href="#" title="
">⌘</a>
 
- What is American National Standards Institute (ANSI)?
<a href="#" title="
The American National Standards Institute (ANSI) is a private non-profit organization that oversees the development of voluntary consensus standards for products, services, processes, systems, and personnel in the United States. The organization also coordinates U.S. standards with international standards so that American products can be used worldwide. American National Standards Institute or ANSI is the organization that developed ASCII. The organization was called American Standards Association's (ASA) back in 1960 when first meetings started. The formation of the organization dates back to 1918. There are around 125,000 companies and 3.5 million professionals as members in 2017.
">⌘</a>
 
- What is the differece between ASCII and ANSI?
<a href="#" title="
">⌘</a>
 
- What is UCS-2?
<a href="#" title="
">⌘</a>
 
- What is UTF-8?
<a href="#" title="
UTF-8 is commonly used encoding that implements Unicode standard. UTF-8 uses one byte for any ASCII character, all of which have the same code values in both UTF-8 and ASCII encoding, and up to four bytes for other characters. In short: Variable length of a character, ASCII characters (the decent-official version of ASCII - range 0 to 127) are still one byte.
">⌘</a>
 
- What is the max UTF-`...` available?
<a href="#" title="
">⌘</a>
 
- What is the difference between UTF-8 and Unicode?
<a href="#" title="
">⌘</a>
 
- What is the difference between UTF-8 and Extended ASCII?
<a href="#" title="
">⌘</a>
 
- What is Byte order mark (BOM)?
<a href="#" title="
">⌘</a>
 
- What is the difference between big-endian and little-endian?
<a href="#" title="
The terms big endian and little endian come originally from Gulliver's Travels. In computer science they refer to the the integer byte-order for a processor. Big endian processors, such as Sparc and PowerPC store the most significant byte in the first memory location of a multi-byte integer. Little endian processors, such as Intel and Alpha do it the other way around. So the 16-bit number 258 (HEX in a decent format: 0x102) would be 0x0102 on big endian and 0x0201 on little endian machines.
">⌘</a>
 
- What is the difference between line feed `LF` (0x0A) and `\n`, or between carriage return `CR` (0x0D) and `\r` ?
<a href="#" title="
CR and LF are ASCII and Unicode control characters while \\r and \\n are abstractions used in certain programming languages. In addition, for example, \n doesn't mean the same thing in all programming languages.
">⌘</a>
 
- What is the difference between NEXT LINE (NEL) (U+0085), Line Separator (LS) (U+2028), and End Of Line (EOL)?
<a href="#" title="
">⌘</a>
 
- What is the default End Of Line (EOL) for each of the following: Windows, Linux, OSX, Unix, older Mac?
<a href="#" title="
 LF - Unix and Unix-like systems (Linux, macOS, FreeBSD, Multics, AIX, Xenix, etc.), BeOS, Amiga, RISC OS; CR+LF - Microsoft Windows, DOS (MS-DOS, PC DOS, etc.), DEC TOPS-10, RT-11, CP/M, MP/M, Atari TOS, OS/2, Symbian OS, Palm OS, Amstrad CPC, and most other early non-Unix and non-IBM OSes; CR - Commodore 8-bit machines, Acorn BBC, ZX Spectrum, TRS-80, Apple II family, Oberon, the classic Mac OS up to version 9, MIT Lisp Machine and OS-9; RS - QNX pre-POSIX implementation; 0x9B - Atari 8-bit machines using ATASCII variant of ASCII (155 in decimal), LF+CR - Acorn BBC and RISC OS spooled text output.
">⌘</a>
 
## Regular expressions
- What is the difference between `[]` and `()`?
<a href="#" title="
">⌘</a>
 
### Security
- What is the difference between authorization and authentication?
<a href="#" title="
">⌘</a>
  
- What is the difference between authorization and ACL?
<a href="#" title="
">⌘</a>
  
- What is challenge-response authentication mechanism (CRAM)?
<a href="#" title="
">⌘</a>
  
- What is Security Support Provider Interface (SSPI)?
<a href="#" title="
">⌘</a>
  
- What is Trusted Authentication?
<a href="#" title="
">⌘</a>
  
- What is Kerberos (protocol) about?
<a href="#" title="
">⌘</a>

- Explain what Transport Layer Security (TLS) is and how it is being used.
<a href="#" title="
">⌘</a>

- Explain what Secure Sockets Layer (SSL) is and how it is being used.
<a href="#" title="
">⌘</a>

- Explain what OpenSSL is and how it is being used.
<a href="#" title="
">⌘</a>

- Explain what Diffie–Hellman key exchange is and how it is being used.
<a href="#" title="
">⌘</a>

- What is the difference between 'Public key' and 'Public key certificate'? Explain dow are they being used.
<a href="#" title="
">⌘</a>

 
### HTML
- Is there any difference between `HTML5` and `HTML 5` (see the space in between)?
<a href="#" title="
">⌘</a>

## Linux
- What is the difference between Unix and Linux?
<a href="#" title="
">⌘</a>
 
- What is \*nix?
<a href="#" title="
">⌘</a>

- What is `man` command for?
<a href="#" title="
">⌘</a>

- Lets say we have all or some `man` pages missing. Can we get and load it, how?
<a href="#" title="
">⌘</a>

- What is the difference between `>` (redirect) and `|` (pipe)?
<a href="#" title="
">⌘</a>

- What is the difference between a hard link and a soft link (aka. symbolic link, symlink, etc.)?
<a href="#" title="
http://linuxgazette.net/105/pitcher.html
">⌘</a>

- What is inode?
<a href="#" title="
http://linuxgazette.net/105/pitcher.html
">⌘</a>

- What is the difference between two special files: '.' and '..'??
<a href="#" title="
http://linuxgazette.net/105/pitcher.html
">⌘</a>


## SQL (Connecting PHP on Linux to Microsoft SQL Server on Windows)
- What is Tabular Data Stream (TDS) about? Applies for SQL products of Microsoft and Sybase.
<a href="#" title="
">⌘</a>

- What is FreeTDS?
<a href="#" title="
FreeTDS is a set of libraries for Unix and Linux that allows programs to natively talk to Microsoft SQL Server and Sybase databases. Technically speaking, FreeTDS is an open source implementation of the TDS (Tabular Data Stream) protocol used by these databases for their own clients. It supports many different flavors of the protocol and three APIs to access it. Additionally FreeTDS works with other software such as Perl and PHP, providing access from those languages as well. FreeTDS has many possible uses. It has been used by Unix/Linux webservers to present data stored in SQL Server to the web, to port SQL Server database code from NT to Unix, to import data into SQL Server from a Unix source, and to provide database access on platforms (such as realtime systems) that have no native drivers. 
">⌘</a>

- Name a few ways (drivers) to connect to Microsoft SQL Server from PHP code hosted on Linux OS?
<a href="#" title="
-`PDO ODBC (aka. PDO_ODBC, pdo-odbc, etc.) driver by community. If it is not possible to use sqlsrv, you can use the PDO_ODBC driver to connect to Microsoft SQL Server and Sybase databases, as the native Windows DB-LIB is ancient, thread un-safe and no longer supported by Microsoft. PDO_ODBC is a driver that implements the PHP Data Objects (PDO) interface to enable access from PHP to databases through ODBC drivers or through the IBM DB2 Call Level Interface (DB2 CLI) library. PDO_ODBC currently (2017) supports three different 'flavours' of database drivers: ibm-db2 (Supports access to IBM DB2 Universal Database, Cloudscape, and Apache Derby servers through the free DB2 client.), unixODBC (Supports access to database servers through the unixODBC driver manager and the database's own ODBC drivers.), generic (Offers a compile option for ODBC driver managers that are not explicitly supported by PDO_ODBC.). On Windows, php_pdo_odbc.dll has to be enabled as extension in php.ini. It is linked against the Windows ODBC Driver Manager so that PHP can connect to any database cataloged as a System DSN, and is the recommended (by PHP) driver for connecting to Microsoft SQL Server databases. More info: http://php.net/manual/en/ref.pdo-odbc.php
-`DBLIB MSSQL PDO driver` (aka. PDO_DBLIB, pdo-dblib, MS SQL Server (PDO), etc.) by (community). PDO_DBLIB is a driver that implements the PHP Data Objects (PDO) interface to enable access from PHP to Microsoft SQL Server and Sybase databases through the FreeTDS library. This extension is not available anymore on Windows with PHP 5.3 or later. This extension could be downloaded from PECL, but the requirement for PHP is version from >=5.0.3 to <= 6.0.0. More info: http://php.net/manual/en/ref.pdo-dblib.php , https://pecl.php.net/package/PDO_DBLIB
-`mssql` driver(-library?) by PHP community (supported till PHP 7.0; as of the release of PHP 5.3, it is no longer available with PECL). At first, in this case, mssql means the driver itself, not 'Microsoft SQL Server'. Driver-related functions in PHP starts with mssql_*. To get these functions to work, you have to compile PHP with --with-mssql[=DIR] , where DIR is the FreeTDS install prefix. And FreeTDS should be compiled using --enable-msdblib. MS SQL functions are aliases to Sybase functions if PHP is compiled with Sybase extension and without MS SQL extension. The mssql driver is built on DB Lib (i.e. it requires ntwdblib.dll) if you are running PHP on Windows. DB Lib is no longer supported by Microsoft. If you are running PHP on Linux, the mssql driver is built on FreeTDS. More info: http://php.net/mssql , https://blogs.msdn.microsoft.com/brian_swan/2010/03/08/mssql-vs-sqlsrv-whats-the-difference-part-1/
-`sqlsrv` (aka. PDO_SQLSRV, pdo-sqlsrv, MS SQL Server (PDO), etc.) - Microsoft's SQL Server Driver for PHP. Available since July of 2008.  Version 2+ gives the PDO functionality as well as the procedural style. Version 4.0+ supports PHP 7.0+ on Windows and Linux (it was Windows-only till 4.0). The SQLSRV extension provides a procedural interface while the PDO_SQLSRV extension implements PDO for accessing data in all editions of SQL Server 2005 and later (including Azure SQL DB). These drivers rely on the Microsoft ODBC. The sqlsrv driver is built, maintained, and supported by Microsoft. The sqlsrv driver is built on ODBC, which is actively maintained by Microsoft and provides access to features in the latest releases of SQL Server. More info: http://sqlsrvphp.codeplex.com/  (July 2008 - October 2013),  https://github.com/Microsoft/msphpsql (July 2008 - now),  https://pecl.php.net/package/sqlsrv  (June 2011 - now),  https://docs.microsoft.com/en-us/sql/connect/php/microsoft-php-driver-for-sql-server
">⌘</a>

- What is ODBC?
<a href="#" title="
">⌘</a>
 
- Anything special about ODBC 3.0?
<a href="#" title="
You had to use SQLConnect(DSN, UID, PWD) to connect to DB before ODBC 3.0, any and all information about the DSN was kept in odbc.ini; You have to use SQLDriverConnect since version 3.0, the connection attributes are provided as a single argument - a string of concatenated name-value pairs, the application can also specify which driver to use and so there is no need for having odbc.ini anymore.
">⌘</a>
   
- What is Data Source Name (DSN)?
<a href="#" title="
">⌘</a>

- What is `DSN-less configuration` in terms of ODBC?
<a href="#" title="
A setup with no odbc.ini, possible since ODBC 3.0.
">⌘</a>

- What is `ODBC-only configuration` in terms of freeTDS?
<a href="#" title="
All connection information is specified in odbc.ini, without the need for freetds.conf. This is the 'traditional' ODBC setup that came true after some progress on the the FreeTDS ODBC library development. For installations that don't need DB-Library and CT-Library, this ODBC-only setup is simpler.
">⌘</a>

- What is `ODBC-combined configuration` in terms of freeTDS?
<a href="#" title="DB-Library and CT-Library configurations are stored in freetds.conf, odbc.ini points to freetds.conf too, - all that allows support for all three FreeTDS libraries in one file. Such configuration in one freetds.conf file is called ODBC-combined configuration. More recently, SQLDriverConnect was added to FreeTDS. This function allows the application to specify connection attributes with reference to either, or neither, configuration file.
">⌘</a>

- What is unixODBC, iODBC, MS ODBC?
<a href="#" title="
All three are ODBC driver managers. For example, unixODBC contains the following components used to assist with the manipulation of ODBC data sources: a driver manager, an installer library and command line tool, command line tools to help install a driver and work with SQL, drivers and driver setup libraries.
">⌘</a>

- What are the functional differences between unixODBC, iODBC, MS ODBC?
<a href="#" title="
http://stackoverflow.com/questions/7548825/what-are-the-functional-differences-between-iodbc-and-unixodbc
">⌘</a>
 
- How to find out which configuration files (for example: `odbc.ini`) unixODBC is using?
<a href="#" title="
Use odbcinst utility.
">⌘</a>

- How to find out which configuration files (for example: `freetds.conf`) freeTDS is using?
<a href="#" title="
Use tsql utility. tsql is a diagnostic tool that uses the lowest level FreeTDS library, libtds, as a way to isolate potential bugs in the protocol implementation.
">⌘</a>

- How to test if unixODBC setup is correct?
<a href="#" title="
You should be able to connect and query a database by using unixODBC's isql utility.
">⌘</a>

- How to test if freeTDS setup is correct?
<a href="#" title="
You should be able to connect and query a database by using freeTDS's tsql utility.
">⌘</a>

- What is TDS connection pooling in terms of FreeTDS?
<a href="#" title="
The FreeTDS connection pool is a server process; it emulates a SQL Server. Any program that can attach to a real SQL Server may instead elect to attach to the pool server. The pool in turn connects to the SQL Server and database you specify, and attempts to share these connections. The Connection Pooling server swims in the src/pool directory. See the src/pool/README for a more detailed description of its inner workings. The FreeTDS connection pool currently only supports TDS version 4.2. This restriction applies to both the client-to-pool and pool-to-server connections!
">⌘</a>

- How can one run TDS connection pooling of FreeTDS?
<a href="#" title="
Edit pool.conf in the FreeTDS's etc directory. Run tdspool with the name (the name should be set in the pool.conf) of the pool you are serving. Before your clients connect to the pool, you must edit your freetds.conf to include the host and port of the pooling server, and point your clients at it.
">⌘</a>

- What is the difference between tsql and t-sql (Transact-SQL)?
<a href="#" title="
tsql - tool by freeTDS for work with freeTDS, for example by quering a database. t-sql, or Transact-SQL, is a set of programming extensions from Sybase and Microsoft that add several features to the Structured Query Language (SQL) including transaction control, exception and error handling, row processing, and declared variables. Microsoft\'s SQL Server and Sybase\'s SQL server support T-SQL statements.
">⌘</a>

- What is the difference between isql and tsql utilities?
<a href="#" title="
isql is tool by unixODBC for work with unixODBC, tsql - tool by freeTDS for work with freeTDS. Both can connect to servers, query databases, etc. Each uses own set of configuration set and so successfully queryng databases with both, unixODBC and freeTDS, means both have correct setups.
">⌘</a>

- What is the difference between isql and iusql?
<a href="#" title="
iusql - Unicode version of isql.
">⌘</a>
 
- What is so special about freeTDS version 8.0 and version 9.0 in the meaning of versioning?
<a href="#" title="
In the earlier days of FreeTDS, Microsoft did not release official specs for the TDS protocol. When MSSQL 2000 (product 8.0) was released, there was semi-official indications from the Microsoft community that the TDS protocol would be version 8.0. So the FreeTDS developers adopted that version for FreeTDS. Years later, when Microsoft started releasing official specs of the protocol, it became obvious that the TDS versions that FreeTDS had labeled 8.0 and 9.0 were actually versions 7.1 and 7.2 respectively. For compatibility reasons version 8.0 is still handled by FreeTDS but you should avoid using it as it could be removed in a future version of FreeTDS or it could clash with a future SQL server version.
">⌘</a>

- Is freeTDS a driver or a library, in case of use for ODBC?
<a href="#" title="
An ODBC driver is a hybrid. For the most part, an application relies on a driver manager to define manifest constants, and links to the library. But because the ODBC specification leaves behavior up to the driver, the application is forced to include the driver's header files, too, to exploit driver-specific functions.
">⌘</a>

- What is the difference between `sqlsrv` driver and `mssql` driver?
<a href="#" title="
mssql and sqlsrv drivers are not one and the same. People are often use mssql and sqlsrv interchangeably, and this is not right. The sqlsrv driver is built, maintained, and supported by Microsoft. The mssql driver is a community-built driver. Few years ago was updated or maintained as an official PHP extension, but as of the release of PHP 5.3, it is no longer available with PECL.
The underlying technologies for the two drivers are different. The sqlsrv driver is built on ODBC, which is actively maintained by Microsoft and provides access to features in the latest releases of SQL Server. The mssql driver is built on DB Lib (i.e. it requires ntwdblib.dll) if you are running PHP on Windows. DB Lib is no longer supported by Microsoft. If you are running PHP on Linux, the mssql driver is built on FreeTDS.
https://blogs.msdn.microsoft.com/brian_swan/2010/03/08/mssql-vs-sqlsrv-whats-the-difference-part-1/
">⌘</a>


## MySQL
- Are table and column names of the database case sensitive?
<a href="#" title="
">⌘</a>

- How do I enable case sesitive or case insensitive search within data?
<a href="#" title="
">⌘</a>

- What is the difference between `LIKE ''` and `= ''`?
<a href="#" title="
">⌘</a>

- What are collations for?
<a href="#" title="
A collation is a set of rules for comparing characters in a character set.
">⌘</a>
 
- What is the difference between collation and encoding?
<a href="#" title="
">⌘</a>

- What is character set?
<a href="#" title="
A character set is a set of symbols and encodings.
">⌘</a>

- What is the difference between character set and encoding?
<a href="#" title="
">⌘</a>

- What is the difference between shared locks (read locks) and exclusive locks (write locks)?
<a href="#" title="
Read locks on a resource are shared, or mutually nonblocking: many clients can read from a resource at the same time and not interfere with each other. Write locks, on the other hand, are exclusive—i.e., they block both read locks and other write locks—because the only safe policy is to have a single client writing to the resource at a given time and to prevent all reads when a client is writing.
In the database world, locking happens all the time: MySQL has to prevent one client from reading a piece of data while another is changing it. It performs this lock management internally in a way that is transparent much of the time.
Write locks also have a higher priority than read locks, so a request for a write lock will advance to the front of the lock queue even if readers are already in the queue (write locks can advance past read locks in the queue, but read locks cannot advance past write locks).
Although storage engines can manage their own locks, MySQL itself also uses a variety of locks that are effectively table-level for various purposes. For instance, the server uses a table-level lock for statements such as ALTER TABLE, regardless of the storage engine.
Source: High Performance MySQL, 3rd Edition (the book)
">⌘</a>
- What is the difference between table-level locking and row-level locking? Storage engines should be mentioned.
<a href="#" title="
The most basic locking strategy available in MySQL, and the one with the lowest overhead, is table locks. Although storage engines can manage their own locks, MySQL itself also uses a variety of locks that are effectively table-level for various purposes. For instance, the server uses a table-level lock for statements such as ALTER TABLE, regardless of the storage engine.
The locking style that offers the greatest concurrency (and carries the greatest overhead) is the use of row locks. Row-level locking, as this strategy is commonly known, is available in the InnoDB and XtraDB storage engines, among others. Row locks are implemented in the storage engine, not the server. The server is completely unaware of locks implemented in the storage engines, the storage engines all implement locking in their own ways.
Source: High Performance MySQL, 3rd Edition (the book)
">⌘</a>
 
 
## Microsoft SQL
- What is the difference between MS SQL (Microsoft SQL) and T-SQL (Transact-SQL)?
<a href="#" title="
">⌘</a>
 
 
# OOP
- What is the difference between a function and a method?
<a href="#" title="
">⌘</a>


# Networks, Internet
- What is Internet Assigned Numbers Authority (IANA) for?
<a href="#" title="
">⌘</a>

- What is `example.org` website for?
<a href="#" title="
">⌘</a>

- What is Multipurpose Internet Mail Extensions (MIME)?
<a href="#" title="
">⌘</a>

- Explain TCP/IP network protocol. What is it all about?
<a href="#" title="
">⌘</a>

- Explain Named Pipe-based SQL connection. What is it about?
<a href="#" title="
">⌘</a>

- What is Distributed Computing Environment / Remote Procedure Calls (DCE/RPC)?
<a href="#" title="
">⌘</a>

- What is Samba (software)?
<a href="#" title="
">⌘</a>

- What is the difference between `DNS domain` and so called `NT domain`?
<a href="#" title="
DNS domains are used for name resolution. NT domains are used for authentication. Authentication is done by the domain controller, often the Primary Domain Controller (PDC).
">⌘</a>

- What is the difference between Primary Domain Controller (PDC) and Backup Domain Controller (BDC)?
<a href="#" title="
A PDC is a Primary Domain Controller, and a BDC is a Backup Domain Controller. You must install a PDC before any other domain servers. The Primary Domain Controller maintains the master copy of the directory database and validates users. A Backup Domain Controller contains a copy of the directory database and can validate users. If the PDC fails then a BDC can be promoted to a PDC. Possible data loss is user changes that have not yet been replicated from the PDC to the BDC. A PDC can be demoted to a BDC if one of the BDC's is promoted to the PDC. Source: http://windowsitpro.com/systems-management/what-pdc-bdc
">⌘</a>

- What is Wireshark software for?
<a href="#" title="
">⌘</a>

 
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

