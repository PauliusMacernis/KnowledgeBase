# Questions
There are some questions that needs to be answered by any senior web developer anytime. You simply cannot fail on these.

## General
- What is the difference between a library and a driver[?](Technically, they're the same thing: bodies of subroutines whose names are exported to a linker (static or runtime). By convention, a "library" is used directly by an application, whose programmer will require documentation and header files. A "driver", by contrast, is defined by a binary API and is used in some kind of framework, hence printer driver and video driver.)

### Encodings
 - What is Unicode[?](Unicode is a computing industry standard for the consistent encoding, representation, and handling of text expressed in most of the world's writing systems. Developed in conjunction with the Universal Coded Character Set (UCS) standard and published as The Unicode Standard. The standard consists of a set of code charts for visual reference, an encoding method and set of standard character encodings, a set of reference data files, and a number of related items, such as character properties, rules for normalization, decomposition, collation, rendering, and bidirectional display order (for the correct display of text containing both right-to-left scripts, such as Arabic and Hebrew, and left-to-right scripts). Unicode can be implemented by different character encodings. The most commonly used encodings are UTF-8, UTF-16 and the now-obsolete UCS-2. We often say "Unicode" when we mean "not ASCII", but that’s silly since of course all of ASCII is also included in Unicode.)
 - What is Unicode Consortium[?](The Unicode Consortium (Unicode Inc.) is a 501(c)(3) type non-profit organization that coordinates the development of the Unicode standard. Its stated goal is to eventually replace existing character encoding schemes with Unicode and its standard Unicode Transformation Format (UTF) schemes, contending that many of the alternative schemes are limited in size and scope, and are incompatible with multilingual environments. Tho Organization cooperates with many standards development organizations, including ISO/IEC JTC1, W3C, IETF, and ECMA. Full members include most of the main computer software and hardware companies with any interest in text-processing standards, including Adobe Systems, Apple, Facebook, Google, Huawei, IBM, Microsoft, Oracle Corporation, Yahoo! and SAP SE.)
 - What is American Standard Code for Information Interchange (ASCII)[?](ASCII, sometimes called US-ASCII, is a character encoding standard. ASCII codes represent text in computers, telecommunications equipment, and other devices. Most modern character-encoding schemes are based on ASCII, although they support many additional characters. ASCII originally based on the English alphabet, ASCII encodes 128 specified characters into seven-bit integers. The characters encoded are numbers 0 to 9, lowercase letters a to z, uppercase letters A to Z, basic punctuation symbols, control codes that originated with Teletype machines, and a space. ASCII includes definitions for 128 characters: 33 are non-printing control characters (many now obsolete) that affect how text and space are processed and 95 printable characters, including the space (which is considered an invisible graphic).)
 - What is the difference between ASCII and US-ASCII[?](No real difference, both are about the same. However, Internet Assigned Numbers Authority (IANA) encourages use of the name "US-ASCII" for Internet uses of ASCII (even if it is a redundant acronym, but the US is needed because of regular confusion of the ASCII term with other 8 bit based character encoding schemes such as Extended ASCII or UTF-8 for example).
 - What is the difference between ASCII and Extended ASCII?
 - What is American National Standards Institute (ANSI)[?](The American National Standards Institute (ANSI) is a private non-profit organization that oversees the development of voluntary consensus standards for products, services, processes, systems, and personnel in the United States. The organization also coordinates U.S. standards with international standards so that American products can be used worldwide. American National Standards Institute or ANSI is the organization that developed ASCII. The organization was called American Standards Association's (ASA) back in 1960 when first meetings started. The formation of the organization dates back to 1918. There are around 125,000 companies and 3.5 million professionals as members in 2017.)
 - What is the differece between ASCII and ANSI[?]()
 - What is UTF-8[?](UTF-8 is commonly used encoding that implements Unicode standard. UTF-8 uses one byte for any ASCII character, all of which have the same code values in both UTF-8 and ASCII encoding, and up to four bytes for other characters. In short: Variable length of a character, ASCII characters are still one byte.)
 - What is the max UTF-`...` available?
 - What is the difference between UTF-8 and Unicode?
 - What is the difference between UTF-8 and Extended ASCII?
 - What is Byte order mark (BOM)?
 - What is the difference between little-endian and big-endian[?](The terms big endian and little endian come originally from Gulliver's Travels. In computer science they refer to the the integer byte-order for a processor. Big endian processors, such as Sparc and PowerPC store the most significant byte in the first memory location of a multi-byte integer. Little endian processors, such as Intel and Alpha do it the other way around. So the 16-bit number 258 (HEX in a decent format:0x102) would be 0x0102 on big endian and 0x0201 on little endian machines.)
 - What is the difference between line feed `LF` (0x0A) and `\n`, or between carriage return `CR` (0x0D) and `\r`[?](CR and LF are ASCII and Unicode control characters while \\r and \\n are abstractions used in certain programming languages. In addition, for example, \n doesn't mean the same thing in all programming languages.)
 - What is the difference between NEXT LINE (NEL) (U+0085), Line Separator (LS) (U+2028), and End Of Line (EOL)?
 - What is the default End Of Line (EOL) for each of the following: Windows, Linux, OSX, Unix, older Mac[?](LF - Unix and Unix-like systems (Linux, macOS, FreeBSD, Multics, AIX, Xenix, etc.), BeOS, Amiga, RISC OS; CR+LF - Microsoft Windows, DOS (MS-DOS, PC DOS, etc.), DEC TOPS-10, RT-11, CP/M, MP/M, Atari TOS, OS/2, Symbian OS, Palm OS, Amstrad CPC, and most other early non-Unix and non-IBM OSes; CR - Commodore 8-bit machines, Acorn BBC, ZX Spectrum, TRS-80, Apple II family, Oberon, the classic Mac OS up to version 9, MIT Lisp Machine and OS-9; RS - QNX pre-POSIX implementation; 0x9B - Atari 8-bit machines using ATASCII variant of ASCII (155 in decimal), LF+CR - Acorn BBC and RISC OS spooled text output.)
 
## Regular expressions
 - What is the difference between `[]` and `()`?
 
### Security
 - What is the difference between authorization and authentication?
 - What is the difference between authorization and ACL?
 
### HTML
 - Is there any difference between `HTML5` and `HTML 5` (see the space in between)?

## Linux
 - What is the difference between Unix and Linux?
 - What is \*nix?
 - What is `man` command for?
 - Lets say we have all or some `man` pages missing. Can we get and load it, how?
 - What is the difference between `>` (redirect) and `|` (pipe) ?

## SQL
 - What is Tabular Data Stream (TDS) about? Applies for SQL products of Microsoft and Sybase.
 - What is ODBC?
 - Anything special about ODBC 3.0 [?](You had to use SQLConnect(DSN, UID, PWD) to connect to DB before ODBC 3.0, any and all information about the DSN was kept in odbc.ini; You have to use SQLDriverConnect since version 3.0, the connection attributes are provided as a single argument - a string of concatenated name-value pairs, the application can also specify which driver to use and so there is no need for having odbc.ini anymore.)
 - What is Data Source Name (DSN)?
 - What is `DSN-less configuration` in terms of ODBC [?](A setup with no odbc.ini, possible since ODBC 3.0)
 - What is `ODBC-only configuration` in terms of freeTDS [?](All connection information is specified in odbc.ini, without the need for freetds.conf. This is the "traditional" ODBC setup that came true after some progress on the the FreeTDS ODBC library development. For installations that don't need DB-Library and CT-Library, this ODBC-only setup is simpler.)
 - What is `ODBC-combined configuration` in terms of freeTDS [?](DB-Library and CT-Library configurations are stored in freetds.conf, odbc.ini points to freetds.conf too, - all that allows support for all three FreeTDS libraries in one file. Such configuration in one freetds.conf file is called ODBC-combined configuration. More recently, SQLDriverConnect was added to FreeTDS. This function allows the application to specify connection attributes with reference to either, or neither, configuration file.)
 - What is unixODBC, iODBC, MS ODBC [?](All three are ODBC driver managers. For example, unixODBC contains the following components used to assist with the manipulation of ODBC data sources: a driver manager, an installer library and command line tool, command line tools to help install a driver and work with SQL, drivers and driver setup libraries.)
 - What are the functional differences between unixODBC, iODBC, MS ODBC[?](http://stackoverflow.com/questions/7548825/what-are-the-functional-differences-between-iodbc-and-unixodbc)
 - How to find out which configuration files (for example: `odbc.ini`) unixODBC is using [?](Use odbcinst utility.)
 - How to find out which configuration files (for example: `freetds.conf`) freeTDS is using [?](Use tsql utility.)
 - How to test if unixODBC setup is correct[?] (You should be able to connect and query a database by using unixODBC's isql utility)
 - How to test if freeTDS setup is correct[?] (You should be able to connect and query a database by using freeTDS's tsql utility)
 - What is the difference between tsql and t-sql (Transact-SQL)[?](tsql - tool by freeTDS for work with freeTDS, for example by quering a database. t-sql, or Transact-SQL, is a set of programming extensions from Sybase and Microsoft that add several features to the Structured Query Language (SQL) including transaction control, exception and error handling, row processing, and declared variables. Microsoft\'s SQL Server and Sybase\'s SQL server support T-SQL statements.)
 - What is the difference between isql and tsql utilities[?](isql is tool by unixODBC for work with unixODBC, tsql - tool by freeTDS for work with freeTDS. Both can connect to servers, query databases, etc. Each uses own set of configuration set and so successfully queryng databases with both, unixODBC and freeTDS, means both have correct setups.)
 - What is the difference between isql and iusql[?](iusql - Unicode version of isql.)
 - What is so special about freeTDS version 8.0 and version 9.0 in the meaning of versioning [?](In the earlier days of FreeTDS, Microsoft did not release official specs for the TDS protocol. When MSSQL 2000 (product 8.0) was released, there was semi-official indications from the Microsoft community that the TDS protocol would be version 8.0. So the FreeTDS developers adopted that version for FreeTDS. Years later, when Microsoft started releasing official specs of the protocol, it became obvious that the TDS versions that FreeTDS had labeled 8.0 and 9.0 were actually versions 7.1 and 7.2 respectively. For compatibility reasons version 8.0 is still handled by FreeTDS but you should avoid using it as it could be removed in a future version of FreeTDS or it could clash with a future SQL server version.)
 - Is freeTDS a driver or a library, in case of use for ODBC [?](An ODBC driver is a hybrid. For the most part, an application relies on a driver manager to define manifest constants, and links to the library. But because the ODBC specification leaves behavior up to the driver, the application is forced to include the driver's header files, too, to exploit driver-specific functions.)

## MySQL
 - Are table and column names of the database case sensitive?
 - How do I enable case sesitive or case insensitive search within data?
 - What is the difference between `LIKE ''` and `= ''`?
 - What are collations for[?](A collation is a set of rules for comparing characters in a character set.)
 - What is the difference between collation and encoding?
 - What is character set[?](A character set is a set of symbols and encodings.)
 - What is the difference between character set and encoding?
 
## Microsoft SQL
 - What is the difference between MS SQL (Microsoft SQL) and T-SQL (Transact-SQL)?
 
# OOP
- What is the difference between a function and a method?

# Internet
- What is Internet Assigned Numbers Authority (IANA) for?
- What is `example.org` website for?
- What is Multipurpose Internet Mail Extensions (MIME)?
 
# PHP
 - Lets say I make HTTPS request to PRODUCTION server. How can I find the most time-consuming code blocks within the project files I am interested in the most?
