# Questions
There are some questions that needs to be answered by any senior web developer anytime. You simply cannot fail on these.

## General
- What is the difference between a library and a driver[?](Technically, they're the same thing: bodies of subroutines whose names are exported to a linker (static or runtime). By convention, a "library" is used directly by an application, whose programmer will require documentation and header files. A "driver", by contrast, is defined by a binary API and is used in some kind of framework, hence printer driver and video driver.)

### Encodings
 - What is ASCII?
 - What is UTF-8?
 - What is the max UTF-`...` available?
 - What is Unicode?
 - What is the difference between UTF-8 and Unicode?
 
## Regular expressions
 - What is the difference between `[]` and `()`?
 
### Security
 - What is the difference between authorization and authentication?
 - What is the difference between authorization and ACL?
 
### HTML
 - Is there any difference between `HTML5` and `HTML 5` (see the space in between)?

## Linux
 - What is the difference between `>` (redirect) and `|` (pipe) ?

## SQL
 - What is Tabular Data Stream (TDS) about? Applies for SQL products of Microsoft and Sybase.
 - What is ODBC?
 - Anything special about ODBC 3.0 [?](You had to use SQLConnect(DSN, UID, PWD) to connect to DB before ODBC 3.0, any and all information about the DSN was kept in odbc.ini; You have to use SQLDriverConnect since version 3.0, the connection attributes are provided as a single argument - a string of concatenated name-value pairs, the application can also specify which driver to use and so there is no need for having odbc.ini anymore.)
 - What is Data Source Name (DSN)?
 - What is `DSN-less configuration` in terms of ODBC [?](A setup with no odbc.ini, possible since ODBC 3.0)
 - What is `ODBC-only configuration` in terms of freeTDS [?](All connection information is specified in odbc.ini, without the need for freetds.conf. This is the "traditional" ODBC setup that came true after some progress on the the FreeTDS ODBC library development. For installations that don't need DB-Library and CT-Library, this ODBC-only setup is simpler.)
 - What is `ODBC-combined configuration` in terms of freeTDS [?](DB-Library and CT-Library configurations are stored in freetds.conf, odbc.ini points to freetds.conf too, - all that allows support for all three FreeTDS libraries in one file. Such configuration in one freetds.conf file is called ODBC-combined configuration. More recently, SQLDriverConnect was added to FreeTDS. This function allows the application to specify connection attributes with reference to either, or neither, configuration file.)
 - What is unixODBC, iODBC, MS ODBC?
 - What are the functional differences between unixODBC, iODBC, MS ODBC[?](http://stackoverflow.com/questions/7548825/what-are-the-functional-differences-between-iodbc-and-unixodbc)
 - How to find out which configuration files (for example: `odbc.ini`) unixODBC is using [?](Use odbcinst utility.)
 - How to find out which configuration files (for example: `freetds.conf`) freeTDS is using [?](Use tsql utility.)
 - What is so special about freeTDS version 8.0 and version 9.0 in the meaning of versioning[?](In the earlier days of FreeTDS, Microsoft did not release official specs for the TDS protocol. When MSSQL 2000 (product 8.0) was released, there was semi-official indications from the Microsoft community that the TDS protocol would be version 8.0. So the FreeTDS developers adopted that version for FreeTDS. Years later, when Microsoft started releasing official specs of the protocol, it became obvious that the TDS versions that FreeTDS had labeled 8.0 and 9.0 were actually versions 7.1 and 7.2 respectively. For compatibility reasons version 8.0 is still handled by FreeTDS but you should avoid using it as it could be removed in a future version of FreeTDS or it could clash with a future SQL server version.)

## MySQL
 - Are table and column names of the database case sensitive?
 - How do I enable case sesitive or case insensitive search within data?
 - What is the difference between `LIKE ''` and `= ''`?
 - What are collations for[?](A collation is a set of rules for comparing characters in a character set.)
 - What is the difference between collation and encoding?
 - What is character set[?](A character set is a set of symbols and encodings.)
 - What is the difference between character set and encoding?
 
