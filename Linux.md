## Linux
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

- **Explain `trap : TERM INT; sleep infinity & wait` found at the end of bash script**  
In short:  
We are running sleep infinitely and then exiting on an interrupt signal.  
In details:  
There might be situations when you don't want users of your scripts to exit untimely using keyboard abort sequences, for example because input has to be provided or cleanup has to be done. The `trap` statement catches these sequences and can be programmed to execute a list of commands upon catching those signals.  
The syntax for the `trap` statement is straightforward: `trap [COMMANDS] [SIGNALS]`  
Read more:  
https://explainshell.com/explain?cmd=trap+%3A+TERM+INT%3B+sleep+infinity+%26+wait  
http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html  
https://bash.cyberciti.biz/guide/Trap_statement  
https://ss64.com/bash/trap.html  
https://stackoverflow.com/questions/13341870/signals-and-interrupts-a-comparison  



Read more:  
https://ss64.com/bash/  
