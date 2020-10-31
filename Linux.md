## Linux
- **What is Linux?**  
Linux is a clone of the operating system Unix, written from scratch by Linus Torvalds with assistance from a loosely-knit team of hackers across the Net. It aims towards POSIX and Single UNIX Specification compliance.  
It has all the features you would expect in a modern fully-fledged Unix, including true multitasking, virtual memory, shared libraries, demand loading, shared copy-on-write executables, proper memory management, and multistack networking including IPv4 and IPv6.  
Although originally developed first for 32-bit x86-based PCs (386 or higher), today Linux also runs on a multitude of other processor architectures, in both 32- and 64-bit variants.  
Read more:  
https://www.kernel.org/linux.html  

- **What is Portable Operating System Interface (POSIX)?**  
Read more:  
https://en.wikipedia.org/wiki/POSIX  

- **What is Single UNIX Specification?**  
Read more:  
http://opengroup.org/unix  
https://blog.opengroup.org/2012/05/17/unix-is-still-as-relevant-as-ever/  

- What is the difference between Unix and Linux?
<a href="#" title="
">⌘</a>
 
- What is \*nix?
<a href="#" title="
">⌘</a>

- What is X Window System?
<a href="#" title="
">⌘</a>

- What is `man` command for?
<a href="#" title="
">⌘</a>

- **Explain `mandb` command. What is it for?**  
`mandb` is used to initialise or manually update index database caches that are usually maintained by `man`. The caches contain information relevant to the current state of the manual page system and the information stored within them is used by the man-db utilities to enhance their speed and functionality.  
Read more:  
http://man7.org/linux/man-pages/man8/mandb.8.html  

- Lets say we have all or some `man` pages missing. Can we get and load it, how?
<a href="#" title="
">⌘</a>

- **What is the difference between `>` and `>>` redirects?**  
Both redirect stdout to file. `ls > list` - if file exists it'll be replaced. `ls >> list` - if file not exists it'll be created, if it exists, it'll be appended to the end of file.  
Read more:  
http://www.tldp.org/LDP/abs/html/io-redirection.html

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

- What is the difference between `*-client`, `*-server` and `*-common` types of packages? For example, there is a line in a team's project saying `Install mariadb via apt-get`. However, `apt-get` finds `mariadb-client`, `mariadb-server` and `mariadb-common` packages only. Which package to install in order to meet the requirement? There is no package called `mariadb` on `apt-get`.
<a href="#" title="">⌘</a>

- **What is `systemd` or `upstart` for?**  
Most current Linux distributions (RHEL, CentOS, Fedora, Ubuntu 16.04 and higher) use `systemd` to manage which services start when the system boots. Ubuntu 14.10 and below use `upstart`.  
For example,  
`sudo systemctl enable docker` starts docker service on system boot,  
`sudo systemctl disable docker` removes docker service from system boot  

- **How can I search the bash history and rerun a command?**  
Type `Ctrl` `R` at the command line and start typing the previous command. Once a result appears keep hitting `Ctrl` `R` to see other matches. When the command you want appears, simply press `Enter`.  
Read more:  
https://superuser.com/questions/7414/how-can-i-search-the-bash-history-and-rerun-a-command  
https://www.gnu.org/software/bash/manual/bashref.html#Commands-For-History  

- **What `service --status-all` does?**  
The `service --status-all` command tries to figure out for every init script in `/etc/init.d` if it supports a `status` command (by grepping the script for `status`).  
If it doesn't find that string it will print `[ ? ]` for that service.  
Otherwise it will run `/etc/init.d/$application status`.  
If the return code is `0` it prints `[ + ]`.  
If it's not `0` it prints `[ - ]`.  
Why may ssh print `[ - ]` even though it's still running?  
`ssh` is controlled by upstart in Ubuntu (13.10).  
Running `/etc/init.d/ssh` status will produce no output and a return code of `1`.  

- **What is TeleTYpewriter (tty)?**  
In computing, `tty` is a command in Unix and Unix-like operating systems to print the file name of the terminal connected to standard input. Given below is a sample output when the command is run.  
```
$ tty
/dev/pts/10
```
Early user terminals connected to computers were electromechanical teleprinters or teletypewriters (TeleTYpewriter, TTY), and since then TTY has continued to be used as the name for the text-only console although now this text-only console is a virtual console not a physical console.  
There are 6 virtual consoles in Ubuntu accessed by the keyboard shortcuts `Ctrl`+`Alt`+`F1` to `Ctrl`+`Alt`+`F6`. You can move away from a virtual console (move the console to the background) by using the keyboard shortcut `Ctrl`+`Alt`+`F7`.  
In Ubuntu 17.10 the login screen now uses virtual terminal `1`. In Ubuntu 17.10 press `Ctrl`+`Alt`+`F3` up to `Ctrl`+`Alt`+`F7` for accessing a virtual console and press `Ctrl`+`Alt`+`F2` to go back to the desktop environment.  
Read more:  
https://askubuntu.com/questions/481906/what-does-tty-stand-for  
https://en.wikipedia.org/wiki/Tty_(unix)  

- **Explain `echo "date.timezone = Europe/Vilnius" >> docker/php/php.ini`**  
The command echos (prints) the string between `""` (and redirects the output) to a file `docker/php/php.ini`.  

- **Explain `mkdir -p .docker/{php,apache}`**  
This will make the directory `.docker` and two subdirectories within: `php` and `apache`.  
The `-p` flag (or alternative: `--parent`) stands for "no error if existing, make parent directories as needed".  
https://ss64.com/bash/mkdir.html  

- **Explain `find . -type f -print | grep php | wc -l`**  
This will find all files in the current directory (`.`). The list will be given to a `grep` command to look for the pattern (`php`). At the very end, lines matching `php` pattern will be given to `wc` utility which will print the newline counts (`-l`).  
Read more:  
https://ss64.com/bash/find.html  
https://ss64.com/bash/grep.html  

- **Explain `chmod -R o+rw bootstrap/ storage/`**  
Read more:  
https://ss64.com/bash/chmod.html  

- **Explain `export PHP_INI_SCAN_DIR=/usr/local/etc/php/conf.d-dev`**  
Sets an environment variable (`PHP_INI_SCAN_DIR` to value `/usr/local/etc/php/conf.d-dev`). Marks each name (e.g. `PHP_INI_SCAN_DIR`) to be passed to child processes in the environment.  
Read more:  
https://ss64.com/bash/export.html  

- **How to make a search in `less`?**  
`/` - type to start writting a pattern  
`n` - for next result  
`N` - for previous result  
Read more:  
https://ss64.com/bash/less.html  

- **What does `chmod +x <filename>` do and how do I use it?**  
`chmod +x` on a file only means, that you'll make it executable.  
The `man` page of `chmod` covers that: `u` stands for user, `g` stands for group, `o` stands for others, `a` stands for all.  
That means that `chmod u+x somefile` will grant only the owner of that file execution permissions whereas `chmod +x somefile` is the same as `chmod a+x somefile`.  
Read more:  
https://askubuntu.com/questions/443789/what-does-chmod-x-filename-do-and-how-do-i-use-it  
https://askubuntu.com/questions/29589/chmod-ux-versus-chmod-x  
https://ss64.com/bash/chmod.html  

- **Explain: `sed -i -e "s/%consumer-key%/$BITBUCKET_CONSUMER_KEY/" app/auth.json`**  
The full format for invoking sed is: `sed OPTIONS... [SCRIPT] [INPUTFILE...]`  
SED is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline).  
While in some ways similar to an editor which permits scripted edits, SED works by making only one pass over the input(s), and is consequently more efficient. But it is SED's ability to filter text in a pipeline which particularly distinguishes it from other types of editors.  
A single command can be specified as the first argument to `sed`. Multiple commands can be specified by using the `-e` or `-f` options. All commands are applied to the input in the order they are specified regardless of their origin.  
...  
`sed` - writes output to standard output.  
`-i` - to edit files in-place instead of printing to standard output.  
`-e script` or `--expression=script` - add the commands in script to the set of commands to be run while processing the input.  
`"s/%consumer-key%/$BITBUCKET_CONSUMER_KEY/"` - sed-comaptible command replacing all occurrences of `%consumer-key%` to `$BITBUCKET_CONSUMER_KEY` (this is the environment variable so the value of the variable will be used).  
`app/auth.json` - the input file to work on.  
Read more:  
https://www.gnu.org/software/sed/manual/sed.html  
https://stackoverflow.com/questions/18527365/what-does-sed-i-option-do  

- **Explain: `chmod -R o+rw the/folder/`**  
Change access permissions, **ch**ange **mod**e of `the/folder/`.  
`-R` (or `--recursive`) - change files and directories recursively.  
`o+rw` - make a file readable and writable by others.   
Read more:  
https://ss64.com/bash/chmod.html  

- **Explain the following:**  
```
curl --silent --show-error --fail --location \
    --header "Accept: application/tar+gzip, application/x-gzip, application/octet-stream" -o - \
    "https://caddyserver.com/download/linux/amd64?plugins=http.expires,http.realip&license=personal" \
    | tar --no-same-owner -C /usr/bin/ -xz caddy \
    && chmod 0755 /usr/bin/caddy \
    && /usr/bin/caddy -version
```
**`curl`** is a tool to transfer data from or to a server, using one of the supported protocols (DICT, FILE, FTP, FTPS, GOPHER, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS, TELNET and TFTP). The command is designed to work without user interaction.  
`curl` offers a busload of useful tricks like proxy support, user authentication, FTP upload, HTTP post, SSL connections, cookies, file transfer resume, Metalink, and more. (To transfer multiple files use wget or FTP.).  
**`--silent`** or `-s` - Silent or quiet mode. Don't show progress meter or error messages. Makes Curl mute. It will still output the data you ask for, potentially even to the terminal/stdout unless you redirect it.  
**`--show-error`** or `-S` - When used with `-s`, `--silent`, it makes `curl` show an error message if it fails.  
**`--fail`** or `-f` - (HTTP) Fail silently (no output at all) on server errors. This is mostly done to better enable scripts etc to better deal with failed attempts. In normal cases when an HTTP server fails to deliver a document, it returns an HTML document stating so (which often also describes why and more). This flag will prevent curl from outputting that and return error 22.  
This method is not fail-safe and there are occasions where non-successful response codes will slip through, especially when authentication is involved (response codes 401 and 407).  
**`--location`** or `-L` - (HTTP) If the server reports that the requested page has moved to a different location (indicated with a Location: header and a 3XX response code), this option will make `curl` redo the request on the new place. If used together with `-i`, `--include` or `-I`, `--head`, headers from all requested pages will be shown. When authentication is used, `curl` only sends its credentials to the initial host. If a redirect takes `curl` to a different host, it won't be able to intercept the user+password. See also `--location-trusted` on how to change this. You can limit the amount of redirects to follow by using the `--max-redirs option`.  
When `curl` follows a redirect and the request is not a plain GET (for example POST or PUT), it will do the following request with a GET if the HTTP response was 301, 302, or 303. If the response code was any other 3xx code, curl will re-send the following request using the same unmodified method.  
You can tell `curl` to not change the non-GET request method to GET after a 30x response by using the dedicated options for that: `--post301`, `--post302` and `--post303`.  
**`--header <header/@file>` (e.g. `--header "Accept: application/tar+gzip, application/x-gzip, application/octet-stream"`)** or `-H` - (HTTP) Extra header to include in the request when sending HTTP to a server. You may specify any number of extra headers. Note that if you should add a custom header that has the same name as one of the internal ones curl would use, your externally set header will be used instead of the internal one. This allows you to make even trickier stuff than `curl` would normally do. You should not replace internally set headers without knowing perfectly well what you're doing. Remove an internal header by giving a replacement without content on the right side of the colon, as in: `-H "Host:"`. If you send the custom header with no-value then its header must be terminated with a semicolon, such as `-H "X-Custom-Header;"` to send "`X-Custom-Header:"`.  
`curl` will make sure that each header you add/replace is sent with the proper end-of-line marker, you should thus not add that as a part of the header content: do not add newlines or carriage returns, they will only mess things up for you.  
Starting in 7.55.0, this option can take an argument in `@filename` style, which then adds a header for each line in the input file. Using `@`- will make curl read the header file from stdin.  
See also the `-A`, `--user-agent` and `-e`, `--referer options`.  
Starting in 7.37.0, you need `--proxy-header` to send custom headers intended for a proxy.  
Example: `curl -H "X-First-Name: Joe" http://example.com/`  
WARNING: headers set with this option will be set in all requests - even after redirects are followed, like when told with `-L`, `--location`. This can lead to the header being sent to other hosts than the original host, so sensitive headers should be used with caution combined with following redirects.  
This option can be used multiple times to add/replace/remove multiple headers.  
**`-o` or `--output <file>`** - Write output to `<file>` instead of `stdout`. If you are using `{}` or `[]` to fetch multiple documents, you can use `#` followed by a number in the `<file>` specifier. That variable will be replaced with the current string for the URL being fetched. Like in: `curl http://{one,two}.example.com -o "file_#1.txt"` or use several variables like: `curl http://{site,host}.host[1-5].com -o "#1_#2"`. You may use this option as many times as the number of URLs you have. For example, if you specify two URLs on the same command line, you can use it like this: `curl -o aa example.com -o bb example.net` and the order of the `-o` options and the URLs doesn't matter, just that the first `-o` is for the first URL and so on, so the above command line can also be written as `curl example.com example.net -o aa -o bb` See also the `--create-dirs` option to create the local directories dynamically.  
**Specifying the output as `-` (a single dash)** - will force the output to be done to stdout. See also `-O`, `--remote-name` and `--remote-name-all` and `-J`, `--remote-header-name`.  
**`"https://caddyserver.com/download/linux/amd64?plugins=http.expires,http.realip&license=personal"`** - the link to download Caddy for linux, using query string parameters to define the Caddy plugins we want to use and the license type. We can adjust the plugins based on our needs by visiting https://caddyserver.com/download and copying the download link after selecting our configuration. We include the `http.expires`, `http.git`, and `http.realip` plugins here.  
**`tar`** - Store, list or extract files in an archive (originally on tape - Tape ARchiver).  
**`--no-same-owner`** - extract files as yourself (default for ordinary users).  
**`-C /usr/bin/`** or `--directory=DIR` - change to directory DIR.  
**`-xz caddy`** - `-x`, `--extract`, `--get`  - extract files from an archive.  
**`-xz caddy`** - `-z` or `--gzip` - filter the archive through gzip.  
**`chmod 0755 /usr/bin/caddy`** - make file `/usr/bin/caddy` permissions like that: user (execute, write, read), group (execute, read), other (execute, read).  
**`/usr/bin/caddy -version`** - Print the version of Caddy (HTTP/2 web server with automatic HTTPS). It also prints build information if not from a tagged release. Caddy will terminate after printing; it does not serve sites if this option is used.  
Read more:  
https://curl.haxx.se/docs/manpage.html  
https://ss64.com/bash/curl.html  
https://linux.die.net/man/1/tar  
https://ss64.com/bash/tar.html  
https://ss64.com/bash/chmod.html  
https://caddyserver.com/docs/cli  
https://caddyserver.com/download  

- **Explain `scp -r -P 20021 -i /home/paulius/.ssh/ uname@example.com:/etc/php5 /home/paulius/dev/example-config/`**  
This will use Secure CoPy command to copy the content of the directory (`/etc/php5`) inside remote machine (`example.com`) to the directory (`/home/paulius/dev/example-config/`) inside the local machine. All files within the directory (`-r`) will be copied by connecting to the remote with the username (`uname`) and public ssh key (`-i`) where the valid public key is about to be found in `/home/paulius/.ssh/` local directory.  
Read more:  
https://www.youtube.com/watch?v=fmMg6cyww14  
https://ss64.com/bash/scp.html  
https://linux.die.net/man/1/scp  

- **Explain `curl -LOk https://github.com/cakephp/cakephp/archive/2.6.0.zip && unzip 2.6.0.zip -d ./ && rm 2.6.0.zip`**  
This downloads the archive ( https://github.com/cakephp/cakephp/archive/2.6.0.zip && unzip 2.6.0.zip ) by using curl. Then the archive is extracted to the same directory ( `./` ) and the original archive file is removed ( `rm 2.6.0.zip` ).  
`curl` is used with three parameters:  
`-L` or `--location` - Follow redirects if the server reports that the requested page has moved (indicated with a Location: header and a 3XX response code).  
`o` or `--output` - Write output to file instead of stdout. If you are using `{}` or `[]` to fetch multiple documents, you can use `#` followed by a number in the file specifier. That variable will be replaced with the current string for the URL being fetched. Like in: `curl https://{one,two}.site.com -o "file_#1.txt"` or use several variables like: `curl https://{site,host}.host[1-5].com -o "#1_#2"`. You may use this option as many times as the number of URLs you have. See also `--create-dirs` option to create the local directories dynamically. Specify `-` to force the output to stdout.  
`k` or `--insecure` - This option explicitly allows curl to perform  "insecure" SSL connections and transfers. All SSL connections are attempted in secure mode using the CA certificate  bundle  installed by  default. This  makes  all connections considered "insecure" fail unless `-k`, `--insecure` is used.(SSL).  
Read more:  
https://ss64.com/bash/curl.html  
https://linux.die.net/man/1/unzip  
https://linux.die.net/man/1/rm  

- **Explain `set -eu` in a bash script**  
Set both `-e` and `-u` so that the script will exit on an Error or if an Unset variable is referenced.  
This is good practice when writing and debugging shell scripts.  
Change the value of a shell option and set the positional parameters, or display the names and values of shell variables.  
If no options or arguments are supplied, set displays the names and values of all shell variables and functions, sorted according to the current locale, in a format that can be reused as input. When options are supplied, they set or unset shell attributes.  
Options: Using `+` rather than `-` will cause the option to be turned off.  
Read more:  
https://ss64.com/bash/set.html  

- **Explain `openssl rand -base64 40`**  
openssl-rand, rand - generate pseudo-random bytes.  
Synopsis: `openssl rand [-help] [-out file] [-rand file...] [-writerand file] [-base64] [-hex] num`  
The rand command outputs num pseudo-random bytes after seeding the random number generator once. As in other openssl command line tools, PRNG seeding uses the file `$HOME/.rnd` or `.rnd` in addition to the files given in the `-rand` option. A new `$HOME/.rnd` or `.rnd` file will be written back if enough seeding was obtained from these sources.  
`-base64` - Perform base64 encoding on the output.  
Read more:  
https://www.openssl.org/docs/manmaster/man1/openssl-rand.html  
https://en.wikipedia.org/wiki/Base64  

- **What is so common about `true` and `:` in Bourne shells (bash)**?  
Historically, Bourne shells didn't have `true` as built-in command. `true` was instead simply aliased to `:`.  
`:` is slightly better than `true` for portability to ancient Bourne-derived shells. As a simple example, consider having neither the `!` pipeline operator nor the `||` list operator (as was the case for some ancient Bourne shells). This leaves the `else` clause of the `if` statement as the only means for branching based on exit status:  
`if command; then :; else ...; fi`  
Since `if` requires a non-empty `then` clause and comments don't count as non-empty, `:` serves as a no-op.  
Nowadays (that is: in a modern context) you can usually use either `:` or `true`. Both are specified by POSIX, and some find `true` easier to read. However there is one interesting difference: `:` is a so-called POSIX ***special built-in***, whereas `true` is a ***regular built-in***.  
  - *Special built-ins* are required to be built into the shell; *Regular built-ins* are only "typically" built in, but it isn't strictly guaranteed. There usually shouldn't be a regular program named `:` with the function of `true` in `PATH` of most systems.
  - Probably the most crucial difference is that with *special built-ins*, any variable set by the built-in - even in the environment during simple command evaluation - persists after the command completes, as demonstrated here using ksh93:
     ```
    $ unset x; ( x=hi :; echo "$x" )
    hi
    $ ( x=hi true; echo "$x" )

    $
    ```
  - Note that Zsh ignores this requirement, as does GNU Bash except when operating in POSIX compatibility mode, but all other major "POSIX sh derived" shells observe this including dash, ksh93, and mksh.
  - Another difference is that *regular built-ins* must be compatible with `exec` - demonstrated here using Bash:
    ```
    $ ( exec : )
    -bash: exec: :: not found
    $ ( exec true )
    $
    ``` 
  - POSIX also explicitly notes that `:` may be faster than `true`, though this is of course an implementation-specific detail.
  
Read more:  
https://stackoverflow.com/questions/3224878/what-is-the-purpose-of-the-colon-gnu-bash-builtin  

- **What is so common about `false` and `let 0` in Bourne shells (bash)?**  
Historically, Bourne shells didn't have `false` as built-in command. `false` was instead simply aliased to something like `let 0`.  
Read more:  
https://stackoverflow.com/questions/3224878/what-is-the-purpose-of-the-colon-gnu-bash-builtin  

- ?? **What is the difference between quoted and not quoted code blocks in bash?**  
Just for example, `:` can also be for block comment (similar to `/* */` in C language). Let say, if you want to skip a block of code in your script, you can do this:  
```
: << SKIP
your code block here
SKIP
```
However, this way command substitutions inside the here document are still processed.  
Anyways, variable resolution/substitution in here docs can be avoided by single-quoting the delimiter:  
```
: << 'SKIP'
your code block here
SKIP
```
Read more:  
https://stackoverflow.com/a/18929997/2026314  

- **What is the difference between Interrupts and Signals on OS like Linux?**  
Interrupts can be viewed as a mean of communication between the CPU and the OS kernel.  
Signals can be viewed as a mean of communication between the OS kernel and OS processes.  
*Interrupts* may be initiated by the CPU (exceptions - e.g.: divide by zero, page fault), devices (hardware interrupts - e.g: input available), or by a CPU instruction (traps - e.g: syscalls, breakpoints). They are eventually managed by the CPU, which "interrupts" the current task, and invokes an OS-kernel provided ISR/interrupt handler.  
*Signals* may be initiated by the OS kernel (e.g: SIGFPE, SIGSEGV, SIGIO), or by a process(kill()). They are eventually managed by the OS kernel, which delivers them to the target thread/process, invoking either a generic action (ignore, terminate, terminate and dump core) or a process-provided signal handler.  
Read more:  
https://stackoverflow.com/questions/13341870/signals-and-interrupts-a-comparison  

- **Explain `man -k signal`**  
`man` - an interface to the on-line reference manuals.  
`-k` - Equivalent to `apropos`. `apropos` - Each manual page has a short description available within it. `apropos` searches the manual page names and descriptions for instances of keyword.  
`signal` - keyword to search for. It is usually a regular expression, as if (`-r`) was used, or may contain wildcards (`-w`), or match the exact keyword (`-e`). Using these options, it may be necessary to quote the keyword or escape (`\`) the special characters to stop the shell from interpreting them. The standard matching rules allow matches to be made against the page name and word boundaries in the description.  
Read more:  
https://ss64.com/bash/man.html  
http://man7.org/linux/man-pages/man1/apropos.1.html  

- **Explain `trap : TERM INT; sleep infinity & wait` found at the end of bash script**  
In short:  
We are running sleep infinitely and then exiting on an interrupt signal.  
In details:  
There might be situations when you don't want users of your scripts to exit untimely using keyboard abort sequences, for example because input has to be provided or cleanup has to be done. The `trap` statement catches these sequences and can be programmed to execute a list of commands upon catching those signals.  
The syntax for the `trap` statement is straightforward: `trap [COMMANDS] [SIGNALS]`  
In the case of our example, all goes like this:  
`trap` - catches the `[SIGNALS]` and runs the `[COMMANDS]` after. When Bash receives a signal for which a trap has been set while waiting for a command to complete, the trap will not be executed until the command completes.  
`:` - a command to execute on signals catch. `:` is equivalent to `true`. Which does nothing except return an exit status of `0`, meaning "success". It can be used as a place holder in shell scripts where a successful command is needed. Although the shell built-in command `:` (colon) does the same thing faster.  
`TERM` - a signal name without `SIG` prefix equivalent to `SIGTERM` and `15` (signal int value). This is Termination signal. The default behavior is to terminate the process, but it also can be caught or ignored. The intention is to kill the process, gracefully or not, but to first allow it a chance to cleanup. The `SIGTERM` signal is a generic signal used to cause program termination. Unlike `SIGKILL`, this signal can be blocked, handled, and ignored. It is the normal way to politely ask a program to terminate. The shell command `kill` generates `SIGTERM` by default.  
`INT` - a signal name without `SIG` prefix equivalent to `SIGINT` and `15` (signal int value). The `SIGINT` (“program interrupt”) signal is sent when the user types the `INTR` character (normally `C`-`c`, most shells bind `Ctrl` + `C` to "send a SIGINT signal to the program that currently runs in the foreground".).  
`;` - When the shell sees a semicolon (`;`) on a command line, it's treated as a command separator -- basically like pressing the ENTER key to execute a command.  
`sleep infinity` - delay for a specified amount of time which is specified as "infinity". TL;DR: `sleep infinity` actually sleeps the maximum time allowed, which is finite.  
`&` - A single ampersand `&` can delimit a list of commands to be run asynchronously. For example, `./script.py & ./script2.py & ./script3.py & `, - all 3 python scripts are run at the same time, in separate sub-shells. Their stdout will still be attached to the parent shell, so if running this from a Linux terminal, you will still see the outputs. This can also be used as a quick hack to take advantage of multiple cores with shell scripts, but be warned, it is a hack!  
`wait` - await process completion.  
When an asynchronous list is started by the shell, the process ID of the last command in each element of the asynchronous list shall become known in the current shell execution environment.  
If the `wait` utility is invoked with no operands, it shall wait until all process IDs known to the invoking shell have terminated and exit with a zero exit status.  
If one or more pid operands are specified that represent known process IDs, the `wait` utility shall wait until all of them have terminated. If one or more pid operands are specified that represent unknown process IDs, `wait` shall treat them as if they were known process IDs that exited with exit status `127`. The exit status returned by the `wait` utility shall be the exit status of the process requested by the last pid operand.  
The known process IDs are applicable only for invocations of wait in the current shell execution environment.  
Read more:  
https://explainshell.com/explain?cmd=trap+%3A+TERM+INT%3B+sleep+infinity+%26+wait  
http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html  
https://bash.cyberciti.biz/guide/Trap_statement  
https://ss64.com/bash/trap.html  
https://stackoverflow.com/questions/13341870/signals-and-interrupts-a-comparison  
https://ss64.com/bash/true.html  
https://linux.die.net/Bash-Beginners-Guide/sect_12_01.html  
https://www.quora.com/What-is-the-difference-between-the-SIGINT-and-SIGTERM-signals-in-Linux-What%E2%80%99s-the-difference-between-the-SIGKILL-and-SIGSTOP-signals  
https://www.gnu.org/software/libc/manual/html_node/Termination-Signals.html  
https://www.gnu.org/software/libc/manual/html_node/Special-Characters.html#Special-Characters  
https://www.gnu.org/software/libc/manual/html_node/Signal-Characters.html  
https://man.cx/signal(7)  
https://superuser.com/questions/243460/what-to-do-when-ctrl-c-cant-kill-a-process  
https://docstore.mik.ua/orelly/unix3/upt/ch28_16.htm  
https://stackoverflow.com/questions/2935183/bash-infinite-sleep-infinite-blocking  
https://github.com/coreutils/coreutils/blob/master/src/sleep.c  
http://bashitout.com/2013/05/18/Ampersands-on-the-command-line.html  
https://man.cx/wait  

- **Does the `exec` command of Bash replace the current process without forking a new process?**  
Yes, it does.  

- **Explain:**  
```
until confd -onetime -backend consul -node consul:8500; do
    echo "Waiting for the initial confd configuration"
    sleep 5
done
```
**`until`**  
The `until` loop is very similar to the `while` loop, except that the loop executes until the `TEST-COMMAND` executes successfully. As long as this command fails, the loop continues. The syntax is the same as for the `while` loop:  
`until TEST-COMMAND; do CONSEQUENT-COMMANDS; done`  
The return status is the exit status of the last command executed in the `CONSEQUENT-COMMANDS` list, or zero if none was executed. `TEST-COMMAND` can, again, be any command that can exit with a success or failure status, and `CONSEQUENT-COMMANDS` can be any UNIX command, script or shell construct.  
**`confd`**  
`confd` is a lightweight configuration management tool that allows you to keep configuration files up to date from data stored in backends like environment variables, Consul (https://www.consul.io/), Etcd (https://github.com/coreos/etcd), Redis (https://redis.io/), and others. You can also reload applications to pick up changes during runtime without restarting the container. With Confd, we can separate our configuration management from infrastructure code.  
**`-onetime`**  
`confd` supports two modes of operation `daemon` and `onetime`. In `daemon` mode `confd` polls a backend for changes and updates destination configuration files if necessary.  
**`-backend consul`**  
we pick `consul` (https://www.consul.io/) as the backend for this case. `confd` supports the following backends: `etcd`, `consul`, `vault`, `env` (environment variables), `redis`, `zookeeper`, `dynamodb`, `rancher`, `ssm` (AWS Simple Systems Manager Parameter Store), etc.  
Consul has multiple components, but as a whole, it is a tool for discovering and configuring services in your infrastructure. It provides several key features: Service Discovery, Health Checking, KV Store (key/value storage), Multi Datacenter.  
**`--node consul:8500`**  
In general, a node is a basic unit used in computer science. Nodes are devices or data points on a larger network. Devices such as a personal computer, cell phone, or printer are nodes. When defining nodes on the internet, a node is anything that has an IP address. Nodes are individual parts of a larger data structure, such as linked lists and tree data structures. Nodes contain data and also may link to other nodes. Links between nodes are often implemented by pointers.  
??? `--node consul:8500` simply points to the Consul service running on exposed port number 8500.  
**`;`**  
The `;` may be replaced with one or more newlines wherever it appears. The semicolon is needed only when the end of line is missing.  
**`do`**  
This is the part of `until` construction.  
**`echo "Waiting for the initial confd configuration"`**  
`echo` is a built-in command in the bash and C shells that writes its arguments to standard output.  
**`sleep 5`**  
Delay for 5 seconds.  
**`done`**  
This is the part of `until` construction.  
Read more:  
http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_03.html  
https://github.com/kelseyhightower/confd  
https://github.com/kelseyhightower/confd/blob/master/docs/quick-start-guide.md  
https://www.consul.io/docs/index.html  
http://www.linfo.org/echo.html  
https://man.cx/sleep  

- **In Bash scripting, what's the meaning of `$!`?**  
The shell treats several parameters specially. These parameters may only be referenced; assignment to them is not allowed. `$` and `!` are a few of these paramters:  
`$` - Expands to the process ID of the shell. In a () subshell, it expands to the process ID of the current shell, not the subshell.  
`!` - Expands to the process ID of the most recently executed background (asynchronous) command.  
So, `$!` contains the process ID of the most recently executed background pipeline.  
Read more:  
https://unix.stackexchange.com/questions/85021/in-bash-scripting-whats-the-meaning-of  
https://linux.die.net/man/1/bash  

- **What does it mean when a command ends with `&`, for example: `php-fpm &`?**  
If a command is terminated by the control operator `&`, the shell executes the command in the background in a subshell. The shell does not wait for the command to finish, and the return status is `0`. Commands separated by a `;` are executed sequentially; the shell waits for each command to terminate in turn. The return status is the exit status of the last command executed.  
Read more:  
https://linux.die.net/man/1/bash  

- **How to create the new folder on Ubuntu 17.10 (hotkey)?**  
`Ctrl` + `Shift` + `N`  
Read more:  
https://ubuntuforums.org/showthread.php?t=1559684  

- **In what order `ssh` obtains configuration data?**  
  1. command-line options
  2. user's configuration file (`~/.ssh/config`)
  3. system-wide configuration file (`/etc/ssh/ssh_config`)

Read more:  
https://man.cx/ssh_config  
  
- **How can I check the keywoards I may use for my `ssh` config file (e.g. `~/.ssh/config`)?**  
`man ssh_config`  
Read more:  
https://man.cx/man  
https://man.cx/ssh_config  

- **Explain `ufw allow 4500/udp`**  
`ufw` − Uncomplicated Firewall (UFW) is a program for managing a netfilter firewall.  
`allow` - add allow rule. To any address on this host.  
`4500/udp` - port `4500` of `udp`.  
Read more:  
https://man.cx/ufw  
https://en.wikipedia.org/wiki/Uncomplicated_Firewall  
https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall  

- **Explain `ssh -p 7822 uname@nlss1.a2hosting.com -L 3306:localhost:3306 -N -v -v`**  
SSH (`ssh`) into `nlss1.a2hosting.com` server by using port 7822 (`-p 7822`) and username `uname`. Forward connection via port 3306 (`-L 3306:localhost:3306`).  
`-N` - Do not execute a remote command. This is useful for just forwarding ports.  
`-v -v` - Verbose mode. Causes `ssh` to print debugging messages about its progress. This is helpful in debugging connection, authentication, and configuration problems. Multiple `−v` options increase the verbosity. The maximum is 3.  
Read more:  
https://man.cx/ssh  

- **Explain: `tag=${1:-latest}` line found in a bash script**  

- **Explain `ACCESS_KEY=$1` line found in a bash script**  

- **Explain `VBoxManage convertdd dd-image.raw sda.vdi --format VDI --variant Fixed`**  
Read more:  
https://www.agix.com.au/use-a-dd-image-as-a-disk-for-a-virtualbox-guest/

- **Explain `man hier`**  
Outputs description of the filesystem hierarchy.  
Read more:  
https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard  
https://man.cx/hier  

- **What is the difference between `apt` and `apt-get` on Ubuntu OS?**  
They are very similar command line tools available in Trusty. `apt-get` and `apt-cache`'s most commonly used commands are available in `apt`.  
`apt-get` may be considered as lower-level and "back-end", and support other APT-based tools. `apt` is designed for end-users (human) and its output may be changed between versions.  
Currently the `apt` binary supports the following commands:
  - `list`: which is similar to `dpkg list` and can be used with flags like `--installed` or `--upgradable`.
  - `search`: works just like `apt-cache search` but sorted alphabetically.
  - `show`: works like `apt-cache show` but hide some details that people are less likely to care about (like the hashes). The full record is still available via `apt-cache show` of course.
  - `update`: just like the regular `apt-get update` with color output enabled.
  - `install`,`remove`: adds progress output during the dpkg run.
  - `upgrade`: the same as `apt-get upgrade --with-new-pkgs`.*
  - `full-upgrade`: a more meaningful name for `dist-upgrade`.
  - `edit-sources`: edit `sources.list` using `$EDITOR`.
 May be worth mentioning that starting in 16.04 by default apt does not save the downloaded packages while apt-get does.
 
- **Explain `sudo dpkg -i libgstreamer*.deb`**  
`sudo` - execute a command as another user (super user).  
`dpkg` - package manager for Debian. `dpkg` is a tool to install, build, remove and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is `aptitude`. `dpkg` itself is controlled entirely via command line parameters, which consist of exactly one action and zero or more options. The action-parameter tells `dpkg` what to do and options control the behavior of the action in some way.  
`-i`, `−−install` - Install the package. If `−−recursive` or `−R` option is speciﬁed, package−ﬁle must refer to adirectory instead.  
`libgstreamer*.deb` - package−ﬁle (matching the given pattern) to install.  
Installation consists of the following steps:  
  1. Extract the control files of the new package.  
  2. If another version of the same package was installed before the new installation, execute `prerm` script of the old package.  
  3. Run `preinst` script, if provided by the package.  
  4. Unpack the new files, and at the same time back up the old files, so that if something goes wrong, they can be restored.  
  5. If another version of the same package was installed before the new installation, execute the `postrm` script of the old package. Note that this script is executed after the `preinst` script of the new package, because new files are written at the same time old files are removed.  
  6. Configure the package. See `−−configure` for detailed information about how this is done.  
Read more:  
https://man.cx/sudo  
https://man.cx/dpkg  

- **What is the `Alt` + `F2` combination for?**  
Run an application by typing its name in the box which appears.  
Read more:  
https://help.ubuntu.com/community/KeyboardShortcuts  

- **What is Magic SysRq key?**  
The magic SysRq key is a key combination understood by the Linux kernel, which allows the user to perform various low-level commands regardless of the system's state. It is often used to recover from freezes, or to reboot a computer without corrupting the filesystem. Its effect is similar to the computer's hardware reset button (or power switch) but with many more options and much more control.  
Read more:  
https://en.wikipedia.org/wiki/Magic_SysRq_key  

- **Explain `docker rm -f angular || true`**  
We try to remove the Docker container. Since the container may not exist, we are using pipes to force true and prevent failure regardless of the scenario.  
`docker` - a computer program that performs operating-system-level virtualization also known as containerization.  
`rm` - remove one or more containers.  
`-f` or `--force` - force the removal of a running container (uses SIGKILL).  
`angular` - the container name.  
`||` -  if the command `docker rm -f angular` has a non-zero exit status, the double pipe OR (`||`) kicks in, and tries to execute the command.  
`true` - the command to execute in case the command `docker rm -f angular` has a non-zero exit status. `true` − do nothing, successfully. Exit with a status code indicating success.  
Read more:  
https://www.thepolyglotdeveloper.com/2017/04/continuous-deployment-of-web-application-containers-with-jenkins-and-docker/  
https://docs.docker.com/engine/reference/commandline/rm/  
https://stackoverflow.com/questions/41625521/bash-which-or-operator-to-use-pipe-v-double-pipe  
https://man.cx/true  

- **Explain the following:**  
```
$ sed ': loop; n; n; n; n; n; n; n; n; n; a GO
n; b loop' < bigfile.sql > bigfile2.sql
```
That inserts a GO every 10 lines (the number of times n appears in the sed script).
Read more:  
https://stackoverflow.com/questions/24665757/sqlcmd-scripting-error  

- **Explain `which sqlcmd`**  
Returns the pathnames of the files (or links) which would be executed in the current environment, had its arguments been given as commands in a strictly POSIX-conformant shell. It does this by searching the PATH for executable files matching the names of the arguments. It does not canonicalize path names.  
Command prompt (Windows OS) alternative would be `where <command-name>`.  
Read more:  
https://man.cx/which  
https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/where_1  

- **What is the difference between semicolon (;) and double ampersand (&&)? For example:**  
`echo "Hello " ; echo "world"`  
and  
`echo "Hello " && echo "world"`  
The ansswer is... `echo "Hello " ; echo "world"` means run `echo "world"` no matter what the exit status of the previous command `echo "Hello"` is i.e. `echo "world"` will run irrespective of success or failure of the command `echo "Hello"`.  
Whereas in case of `echo "Hello " && echo "world"`, `echo "world"` will only run if the first command (`echo "Hello"`) is a success (i.e. exit status 0).  
The following commands give an example of how the shell handles commands chaining using the different operators:  
<pre><code>$ false ; echo "OK"
OK
$ true ; echo "OK"
OK
$ false && echo "OK"
$ true && echo "OK"
OK
$ false || echo "OK"
OK
$ true || echo "OK"
$
</code></pre>
Read more:  
https://unix.stackexchange.com/questions/187145/whats-the-difference-between-semicolon-and-double-ampersand  

- **What is the difference between cron and crontab?**  
**cron** is the general name for the service that runs scheduled actions.  
**crond** is the name of the daemon that runs in the background and reads **crontab** files.  
A **crontab** is a file containing jobs in the format `minute hour day-of-month month day-of-week	command` crontabs are normally stored by the system in `/var/spool/<username>/crontab`. These files are not meant to be edited directly. You can use the **`crontab`** command to invoke a text editor (what you have defined for the EDITOR env variable) to modify a crontab file.  
There are various implementations of **cron**. Commonly there will be per-user crontab files (accessed with the command `crontab -e`) as well as system crontabs in `/etc/cron.daily`, `/etc/cron.hourly`, etc.  
In your first example you are scheduling a job via a crontab. In your second example you're using the `at` command to queue a job for later execution.  
Read more:  
https://stackoverflow.com/questions/21789148/difference-between-cron-and-crontab  

- **Explain `sudo nautlius`**  
`nautilus` is a file manager in Ubuntu.  
`sudo` is declaring that you are a root (it is something like an adminstrator in Windows).  
So, when you type the command `sudo nautilus`, you are entering the file manager as a root. Being root gives you some extra abilities that normal user doesn't have.  
Read more:  
https://askubuntu.com/questions/658058/what-is-sudo-nautilus-what-does-it-do-when-do-i-use-it  

- **What is the difference between `ln -s /path/to/file /path/to/symlink` and `ln -sf /path/to/file /path/to/symlink`?**  
Both creates symlink. However, `ln -s /path/to/file /path/to/symlink` is for creating the new one (will fail if symlink exists already) while `ln -sf /path/to/file /path/to/symlink` is for create or update symlink.  
`−s`, `−−symbolic` - make symbolic links instead of hard links.  
`−f`, `−−force` - remove existing destination files.  
Read more:  
https://stackoverflow.com/questions/1951742/how-to-symlink-a-file-in-linux  
https://man.cx/ln  

- **How to create a symlink shown as `/home/aukok/www -> /var/www/aukok` at the time of listing (`ls -al`)?**  
`mkdir -p /home/aukok` - create the parent directory (required).  
`ln -sf /var/www/aukok /home/aukok/www` - make a symlink (`-f` is optional because we just created the new empty parent directory).  
Read more:  
https://stackoverflow.com/questions/1951742/how-to-symlink-a-file-in-linux   
https://man.cx/ln  

- **Explain: `echo $0`**  
This will tell which shell is being used on the Linux box.  
The shell treats several parameters specially. These parameters may only be referenced; assignment to them is not allowed.  
($0) Expands to the name of the shell or shell script. This is set at shell initialization. If Bash is invoked with a file of commands, $0 is set to the name of that file. If Bash is started with the -c option (see Invoking Bash), then $0 is set to the first argument after the string to be executed, if one is present. Otherwise, it is set to the filename used to invoke Bash, as given by argument zero.  
Read more:  
https://www.gnu.org/software/bash/manual/bash.html#Special-Parameters  
https://www.gnu.org/software/bash/manual/bash.html#Shell-Scripts  
https://www.gnu.org/software/bash/manual/bash.html#Invoking-Bash  

- **Explain `whoami`**  
Print the user name associated with the current effective user ID. Same as `id −un`.  
Simply saying, it prints the username.  
Read more:  
https://man.cx/whoami  

- **What kind of variable types do bash support?**  
Unlike many other programming languages, Bash does not segregate its variables by "type." Essentially, Bash variables are character strings, but, depending on context, Bash permits arithmetic operations and comparisons on variables. The determining factor is whether the value of a variable contains only digits.  
Read more:  
http://tldp.org/LDP/abs/html/untyped.html  

- **Which of the following is correct: `if [ $MY_VARIABLE = 1 ];` or `if [$MY_VARIABLE = 1];` while bash scripting?**  
First obvious thing is you should provide spaces between the arguments of `[`, `test` or `[[`.  
Read more:  
https://unix.stackexchange.com/questions/149203/why-is-the-if-1-1-branch-always-selected-even-if-1-is-not-1  

- **Explain: `install -Dv /dev/null some/new/path/base-filename`**  
TBD  
Read more:  
https://stackoverflow.com/questions/24666330/bash-command-to-create-a-new-file-and-its-parent-directories-if-necessary  
https://man.cx/install  

- **Explain: `script.sh &`**  
To run a shell script (`script.sh`) in background (`&`).  
Read more:  
https://askubuntu.com/questions/88091/how-to-run-a-shell-script-in-background  

- **Explain: `x-terminal-emulator`**  
Read more:  
https://askubuntu.com/questions/46627/how-can-i-make-a-script-that-opens-terminal-windows-and-executes-commands-in-the  

- **Explain: `alias rxvt='urxvt -fg '"'"'#111111'"'"' -bg '"'"'#111111'"'"`**  
Read more:  
https://stackoverflow.com/questions/1250079/how-to-escape-single-quotes-within-single-quoted-strings  

- **Explain `youtube-dl --ignore-errors --extract-audio --audio-format mp3 -o "%(title)s.%(ext)s" https://www.youtube.com/playlist?list=PLdYFKR1OyeXI9A91oVeFVg_H-yOPZfQVw`**  
Read more:  
https://askubuntu.com/questions/564567/how-to-download-playlist-from-youtube-dl  

- **Create the dir, cd into it, `pwd` shows the correct dir path, remove the dir with another tool (like Nautilus file manager), create the same dir (the same dir name) with the same tool (like Nautilus) again, get back to the previous terminal window and run `ls -al` - the dot files (`.` and `..`) are gone. What happened?**  
??something related to inodes?  
Read more:  
???  

- **What is "systemd journal" command for (e.g. on Ubuntu)?**  
systemd-journald.service, systemd-journald.socket, systemd-journald-dev-log.socket, systemd-journald-audit.socket, systemd-journald — Journal service.  
systemd-journald is a system service that collects and stores logging data. It creates and maintains structured, indexed journals based on logging information that is received from a variety of sources: 
  - Kernel log messages, via kmsg
  - Simple system log messages, via the libc syslog(3) call
  - Structured system log messages via the native Journal API, see sd_journal_print(4)
  - Standard output and standard error of service units.
  - Audit records, originating from the kernel audit subsystem
  
  Read more:  
  https://www.freedesktop.org/software/systemd/man/systemd-journald.service.html  
  https://man.cx/journalctl  

- **What does the command `find  . -type d  -user root` do?**  
It looks inside the current directory (`.`) and recursively finds all directories (`-type d`) owned by user root (`-user root`).  
Read more:  
https://man.cx/find  

- **Explain `nohup sudo -u www-data php -d memory_limit=7G /srv/www/bin/console systemx:import:images &`**  
Read more:  
https://man.cx/nohup  
https://unix.stackexchange.com/questions/3886/difference-between-nohup-disown-and  
http://php.net/manual/en/features.commandline.options.php  

- **Explain `curl -D- -u username:password <rest-of-request>`**  
`-D`, `--dump-header` <file>
 Write the protocol headers to the specified file. This  option is handy to use when you want to store the headers that a HTTP site sends to you. C  
 After a `-D` you normally give the name of the file where you want to dump the headers. As with many utilities, `-` is recognized as an alias to stdout.  
 (if you're not familiar with that concept: when you launch the command from a terminal without redirection, stdout is the "terminal screen")  
 The `-D-` (without space) form is exactly the same as `-D -` (or on Linux at least, `-D /dev/stdout`).  
 Read more:  
 https://stackoverflow.com/questions/25017476/curl-d-option  
 
- **Does " - " mean stdout in bash? For example: `wget -q -O - $line`**  
It's just a convention of many UNIX command line utilities to accept `-` as a placeholder for `stdin` or `stdout` when put in place of an input or output file name on the command line.  
Read more:  
https://stackoverflow.com/questions/3797795/does-mean-stdout-in-bash  
http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap12.html#tag_12_02  

- **Explain `sudo bash -c "sleep 1h; pm-suspend"`**  
Suspend the machine after 1 hour.  
Read more:  
https://askubuntu.com/questions/1792/how-can-i-suspend-hibernate-from-command-line/131022#131022  

- **Explain: `setsid myscript.sh >/dev/null 2>&1 < /dev/null &`**  
Read more:  
https://stackoverflow.com/questions/19233529/run-bash-script-as-daemon  

- **What is the fifference between `nm-applet &` and `nm-applet & exit`?**  
Read more:  
https://askubuntu.com/a/106910  

- **What does `ssh-keygen -lf /path/to/ssh/key` do?**  
Gets fingerprint of the file `/path/to/ssh/key`  
Read more:  
https://man.cx/ssh-keygen  
https://stackoverflow.com/questions/9607295/how-do-i-find-my-rsa-key-fingerprint  

- **Explain `getconf ARG_MAX`**  
Get command argument limit in bytes.  
Read more:  
https://stackoverflow.com/questions/19354870/bash-command-line-and-input-limit  

- **Explain `paste -s -d ',' input.csv > output.txt`**  
Merges lines of `input.csv` file by injecting `,` in between of all merged lines. The result is sent to `output.txt`  
Read more:  
https://unix.stackexchange.com/questions/114244/replace-all-newlines-to-space-except-the-last  
https://man.cx/paste  

- **Explain `getfacl .`**  
???  
Read more:  
https://linux.die.net/man/1/setfacl  
https://linux.die.net/man/1/getfacl  

- **Explain `truncate --size 0 logfile`**  
Shrinks (or extends?) the size of a file to the specified size - 0 bytes.
Read more:  
https://man.cx/truncate  

- **What is the difference between `sudo find . -name "*" -delete` and `rm -f *`?**  
Read more:  
https://stackoverflow.com/questions/11289551/argument-list-too-long-error-for-rm-cp-mv-commands  

- **Explain `grep -rnw '/path/to/somewhere/' -e 'pattern'`**  
Read more:  
https://stackoverflow.com/questions/16956810/how-do-i-find-all-files-containing-specific-text-on-linux  
  
- **Explain `=~` used in bash test, for example: `if [[ $save =~ e ]]`**  
Read more:  
https://unix.stackexchange.com/questions/340440/bash-test-what-does-do/340485  
http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29  
  
- **Explain `echo $-` used in bash script**  
Prints the values of the shell's flags. You can set and unset such flags with `set`, e.g. `set -e` (will exit the script if error) or `set +e` (will NOT exit the script if error).  
Read more:  
https://unix.stackexchange.com/questions/315829/how-to-understand-the-output-of-echo  
https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_05_02  

- **Explain `df -Ph .`**  
Shows current directory info, including the usead and available space, space usage in percents, where the directory is mounted on, etc.  
`df` - report file system disk space usage  
`-P, --portability` - use the POSIX output format  
`-h, --human-readable` - print sizes in powers of 1024 (e.g., 1023M)  
Outouts something like this on one line:  
`Filesystem      Size  Used Avail Use% Mounted on`  
And this on the next one:  
`/dev/nvme0n1p2  234G  172G   50G  78% /`   
Read more:  
https://unix.stackexchange.com/questions/6008/get-the-free-space-available-in-current-directory-in-bash  


- **Explain `diff -qr old/ new/`**  
TBD  


