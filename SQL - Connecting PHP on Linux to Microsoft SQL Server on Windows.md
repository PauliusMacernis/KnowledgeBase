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
-`sqlsrv` (aka. PDO_SQLSRV, pdo-sqlsrv, MS SQL Server (PDO), etc.) - Microsoft's SQL Server Driver for PHP. Available since July of 2008.  Version 2+ gives the PDO functionality as well as the procedural style. Version 4.0+ supports PHP 7.0+ on Windows and Linux (it was Windows-only till 4.0). The SQLSRV extension provides a procedural interface while the PDO_SQLSRV extension implements PDO for accessing data in all editions of SQL Server 2005 and later (including Azure SQL DB). These drivers rely on the Microsoft ODBC. Microsoft Drivers for PHP for SQL Server version 3.1 and later support SQL Server 2008 and later. Microsoft Drivers for PHP for SQL Server version 2.0 and 3.0 support SQL Server 2005 and later. The sqlsrv driver is built, maintained, and supported by Microsoft. The sqlsrv driver is built on ODBC, which is actively maintained by Microsoft and provides access to features in the latest releases of SQL Server. More info: http://sqlsrvphp.codeplex.com/  (July 2008 - October 2013),  https://github.com/Microsoft/msphpsql (July 2008 - now),  https://pecl.php.net/package/sqlsrv  (June 2011 - now),  https://docs.microsoft.com/en-us/sql/connect/php/microsoft-php-driver-for-sql-server
">⌘</a>

- What is DB-lib (aka. dblib) by Microsoft?
<a href="#" title="
">⌘</a>

- What is ODBC?
<a href="#" title="
More info: https://github.com/Microsoft/ODBC-Specification , http://searchoracle.techtarget.com/definition/Open-Database-Connectivity
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
