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
- What are index prefixes?
<a href="#" title="
They are indexes build upon a prefix of the column's data. http://www.mysqldba.co.uk/articles/what-are-index-prefixes
">⌘</a>  

- **How to reset MySQL root password?**  
Read more: 
https://linuxconfig.org/how-to-reset-root-mysql-password-on-ubuntu-18-04-bionic-beaver-linux   

