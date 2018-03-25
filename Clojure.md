- **What is Clojure?**  
Clojure ( /ˈkloʊʒɜːr/, like "closure") is a dialect of the Lisp programming language. Clojure is a general-purpose programming language with an emphasis on functional programming. It runs on the Java virtual machine and the Common Language Runtime. There is a dialect, developed in lockstep with Clojure, called ClojureScript, that compiles to ECMAScript 3. Like other Lisps, Clojure treats code as data and has a macro system. The current development process is community-driven, overseen by Rich Hickey as its benevolent dictator for life (BDFL).  
  
- **What is Lisp programming language?***  
Lisp (historically, LISP) is a family of computer programming languages with a long history and a distinctive, fully parenthesized prefix notation. Originally specified in 1958, Lisp is the second-oldest high-level programming language in widespread use today. Only Fortran is older, by one year. Lisp has changed since its early days, and many dialects have existed over its history (Arc, AutoLISP, Clojure, Common Lisp, Emacs Lisp, EuLisp, Franz Lisp, Hy, Interlisp, ISLISP, LeLisp, LFE, Maclisp, MDL, newLISP, NIL, Picolisp, Portable, Standard Lisp, Racket, RPL, Scheme, SKILL, Spice Lisp, T, Zetalisp). Lisp was originally created as a practical mathematical notation for computer programs, influenced by the notation of Alonzo Church's lambda calculus. It quickly became the favored programming language for artificial intelligence (AI) research. As one of the earliest programming languages, Lisp pioneered many ideas in computer science, including tree data structures, automatic storage management, dynamic typing, conditionals, higher-order functions, recursion, the self-hosting compiler, and the read–eval–print loop (REPL). The name LISP derives from "*LISt Processor*". Linked lists are one of Lisp's major data structures, and Lisp source code is made of lists. Thus, Lisp programs can manipulate source code as a data structure, giving rise to the macro systems that allow programmers to create new syntax or new domain-specific languages embedded in Lisp.  
Lisp was invented by John McCarthy in 1958 while he was at the Massachusetts Institute of Technology (MIT). McCarthy published its design in a paper in Communications of the ACM in 1960, entitled "Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I". He showed that with a few simple operators and a notation for functions, one can build a *Turing-complete language for algorithms*.  

- **What is Clojars ( https://clojars.org/ ) for?**  
  It is community repository for open source Clojure libraries.
  
  - **What is Leiningen ( https://leiningen.org/ )?**  
   Leiningen is the Clojure counterpart of Maven, a popular Java build tool. It uses a Maven-compatible dependency management system, and therefore it has access to large and well-maintained repositories of Java libraries. In addition, Clojure libraries are commonly found in the Clojars repository. This repository is enabled by default in Leiningen.  
In general, Leiningen is a tool for working with Clojure projects.  
   
 - **What can be done with Leiningen's `lein` command?**  
```
change              Rewrite project.clj by applying a function.
check               Check syntax and warn on reflection.
classpath           Print the classpath of the current project.
clean               Remove all files from project's target-path.
compile             Compile Clojure source into .class files.
deploy              Build and deploy jar to remote repository.
deps                Download all dependencies.
do                  Higher-order task to perform other tasks in succession.
help                Display a list of tasks or help for a given task.
immutant            Tasks for managing Immutant 2.x projects in a WildFly container.
install             Install the current project to the local repository.
jar                 Package up all the project's files into a jar file.
javac               Compile Java source files.
migratus            Maintain database migrations.
new                 Generate project scaffolding based on a template.
plugin              DEPRECATED. Please use the :user profile instead.
pom                 Write a pom.xml file to disk for Maven interoperability.
release             Perform :release-tasks.
repl                Start a repl session either with the current project or standalone.
retest              Run only the test namespaces which failed last time around.
run                 Run a -main function with optional command-line arguments.
search              Search Central and Clojars for published artifacts.
show-profiles       List all available profiles or display one if given an argument.
test                Run the project's tests.
test-refresh        Autoruns clojure.test tests on source change or
trampoline          Run a task without nesting the project's JVM inside Leiningen's.
uberjar             Package up the project files and dependencies into a jar file.
update-in           Perform arbitrary transformations on your project map.
upgrade             Upgrade Leiningen to specified version or latest stable.
vcs                 Interact with the version control system.
version             Print version for Leiningen and the current JVM.
with-profile        Apply the given task with the profile(s) specified.
```
   
- **What is Luminus ( http://www.luminusweb.net/ )?**  
  Luminus is a Clojure micro-framework based on a set of lightweight libraries.
  
- **What is H2 (DBMS) ( http://www.h2database.com/ )?**  
  H2 is a relational database management system written in Java. It can be embedded in Java applications or run in the client-server mode.
  
- **How to run the new Luminus +H2 project on Linux (e.g. Ubuntu)?**  
1. Place the following code into: `/home/__USER__/.lein/profiles.clj` to follow the same lein-template version:
```{:user
 {:plugins [[luminus/lein-template "2.9.10.74"]]}}
```
2. Run `lein new luminus guestbook +h2` to create a new application by specifying luminus as the template name and guestbook as the project name, and add the +h2 parameter to indicate that we want to have an instance of the H2 embedded database initialized for us.  
3. Run `lein run -p 8000` to start the application on port 8000. When you run the application, it may take a little while because Leiningen first has to retrieve all of its dependencies. Once downloaded, the dependencies are cached locally in the `~/.m2/repository` folder and will be available on subsequent runs.
4. Open a web browser and check for `http://localhost:8000/`

- **How to create migration files (_datetime_-guestbook.up.sql & _datetime_-guestbook.down.sql) by using `lein`?**  
  `lein migratus create guestbook`
  
- **How to run migrations by using `lein`?**  
  `lein run migrate`
  
- **What are SQL template files used by the HugSQL library (files generated by default when creating luminus project)?**  
  A new luminus project contains a file called `resources/sql/queries.sql`. This file is already populated with some sample query templates. The function names are specified using the `-- :name` comment followed by hints indicating the type of query, and the parameters are prefixed with the `:`. The `-- :doc` comment is used to generate the documentation metadata for the function. Otherwise, the queries are written using regular SQL syntax.  
```
-- :name get-user :? :1
-- :doc retrieve a user given the id.
SELECT * FROM users
WHERE id = :id
```
- **What kind of flags exists within SQL templates by the HugSQL?**  
  `:!` - the query is destructive (update, delete, insert)  
  `:n` - the query returns the number of affected rows (update, delete, insert)  
  `:?` - the query does a select  
  `:*` - the query returns multiple rows  
  `:1` - the query returns one row (@TODO: check if this is true)  
  
- **How does the file `resources/sql/queries.sql` get read (files generated by default when creating luminus project with H2)?**  
  The `projectname.db.core` namespace contains a call to the `conman.core/bind-connection` macro. This macro reads the SQL queries that we defined in `resources/sql/queries.sql` and creates Clojure functions that call them using the name specified using the `-- :name` comment.
  
- **What is `profiles.clj` file (luminus project) for ?**  
The profiles.clj file contains information about the local environment that’s not meant to be checked into the shared code repository. Database connection parameters are an example of such environment variables.

- **What is `Mount library` (https://github.com/tolitius/mount) for?**  
Mount library is for managing Clojure and ClojureScript app state since (reset).  
If Clojure REPL (i.e. lein repl, boot repl) fired up instantly, the need to reload application state inside the REPL would go away. But at the moment, and for some time in the future, managing state by making it reloadable within the same REPL session is important to retain all the Clojure superpowers.
  
- **Are queries in `resources/sql/queries.sql` sanitized to prevent SQL injections if `:variable`-alike values are being used? (default luminus project)**  
  Since the queries are parameterized, any variables we pass in are sanitized to prevent SQL injection.
  
- **What is network REPL (nREPL) server?**  
  ~~nREPL stands for "network REPL", and while this may sound pretty similar to a "socket REPL", they are completely different animals.
  The REPLs we've seen so far are stream based, they read lines from an input stream, and write the result (and any output from side effects) to an output stream. This makes them conceptually simple, but tedious to communicate with programmatically.
  nREPL seeks to fix this by being message-based, putting program-to-program first through a client-server architecture, where the client is your editor or IDE, and the server is the nREPL "REPL".
  The client initiates the interaction by sending a message to the server, and as a response the server will send one or more messages back to the client.
  The easiest way to start an nREPL server is either through Leiningen (lein repl) or Boot (boot repl). In either case the first line of output will contain a port number that an nREPL client can connect to.
    
- **Is nREPL server being run on the dev server by default in the new luminus project?**  
  When the application starts in development mode, it automatically runs the nREPL server on port 7000. We can connect to this REPL and inspect the running application: `lein repl :connect 7000`
  
- **Can REPL be run (`lein repl :connect 7000`) without running the application (`lein run -p 8000`)?**  
No. Run the application at first.  
   
- **What is the file `env/dev/clj/user.clj` for (in the new luminus project)?**  
  The REPL starts in the user namespace that’s found at the env/dev/clj/user.clj file. This namespace is reserved for any development code that we wouldn’t want to package in our application. It also provides a scratch pad where we can try things out. This namespace provides start and stop helper functions that allow us to control the state of the application.
  
- **Is it neccessary to restart the application after each change (in the new luminus project)?**  
   There are a few cases where we will need to restart the application. The most common reason is when we’re adding new dependencies to the project, as those can’t be loaded dynamically by the JVM. However, if we think our application has got in a bad state, then we may wish to restart it as well.  
   
 - **How to run a query-template (SQL) without parameters involved in nREPL (in the new luminus project)?**  
   `(query-name)`
   
 - **How to check the documentation of any query-template (SQL) in nREPL (in the new luminus project)?**  
   `(doc query-name)`
   
 - **How to run a query-template (SQL) with parameters involved in nREPL (in the new luminus project)?**  
   For example:
```
   (save-message! {:name "John Smith"
 	                :email "info@example.com"
 	                :timestamp (java.util.Date.)})
```
  
 - **How to run tests via lein (in the new luminus project)?**  
  `lein test`
  
 - **What is Leiningen plugin called `lein-test-refresh` (https://github.com/jakemcc/lein-test-refresh) for?**  
  If we have some tests then we can use a Leiningen plugin called lein-test-refresh to run them automatically any time we update the code in the project. This plugin is part of the Luminus template. 
  
 - **Why a development with `lein test-refresh` running is better than Test-driven development (TDD) ?**  
   We can keep an eye on this terminal to make sure that all our tests are passing whenever we make changes to the code or add new tests. This provides us with an automated sanity check that everything is working as expected.  
   Developing the functionality using the REPL and then generating the tests is a common workflow in Clojure. This approach provides a faster feedback loop than Test Driven Development (TDD) since we don’t have to constantly switch between tests and code while developing a feature. **Instead, the development can be done interactively using the REPL. Once the feature works as desired, then we can take the code from the REPL session and turn it into unit tests for this feature.(???)**  
   https://stackoverflow.com/questions/17891868/the-right-way-to-run-unit-tests-in-clojure
   
- **Where are static assets like CSS put (the new luminus project)?**  
  Static assets such as CSS, images, and JavaScript are found in the `resources/public` folder.  
  
- **Do we need to define routes for static assests we put to `resources/public` folder (the new luminus project)?**  
  Assets of this folder are served without the need to define routes for them.  
  
- **Which library is the default one handeling input validation in the new luminus project?**  
   Luminus defaults to using the Bouncer library ( https://github.com/leonardoborges/bouncer ) to handle input validation. The library provides a straightforward way to check that our parameter map contains the required values.  
   Bouncer uses `bouncer.core/validate` and `bouncer.core/valid?` functions for handling validation. These functions each accept a map containing the parameters followed by the validators. The former will validate the input and return error messages for any invalid fields, while the latter returns a Boolean value indicating whether the input is valid. 
   The result of the validate function is a vector where the first element is either nil when the validation passes or it is a map of errors. The keys in the map are the parameters that failed validation and the values are the error messages.  
   
- **What is vector notation about in Clojure?**  
  Vectors are sequential, indexed, heterogeneous collections. Indexing is 0-based.  
  More info: https://clojure.org/reference/data_structures#Vectors  
  An example of retrieving the value at index 1 in a vector of three values:  
```
user=> (get ["a" 13.7 :foo] 1)
13.7
```
    
- **How to package an app (luminus-based project) into a runnable JAR?**  
   `lein uberjar`  
   The archive will be created in the `target` folder of an application, run it using the `java` command.  
   
 - **How to package an app (luminus-based project) into a runnable JAR with DB support (environment variables set as needed)?**  
    Since we're using a database, we also have to make sure that the connection is specified as an environment variable. When we ran our application in development mode, the connection variable was provided in the `profiles.clj` file. However, now that the application has been packaged for production, this variable is no longer available. Let's create a connection variable and then run our application as follows:  
    `export DATABASE_URL="jdbc:h2:./guestbook_dev.db"`  
    `java -jar target/uberjar/guestbook.jar -p 8000`
    
- **Do you know any Clojure-aware IDE?**  
    - Light Table ( http://lighttable.com/ )  
    - Emacs ( https://www.gnu.org/software/emacs/ )  
    - Cursive ( https://cursive-ide.com/ )  
    - Counterclockwise ( https://github.com/ccw-ide )  


   
  
  
  - **Read more**  
  https://en.wikipedia.org/wiki/Lisp_machine  
  http://blog.ndk.io/clojure-bootstrapping.html  
  https://lambdaisland.com/guides/clojure-repls  
  https://mitpress.mit.edu/sicp/full-text/book/book.html  
  https://github.com/jakemcc/lein-test-refresh
  
