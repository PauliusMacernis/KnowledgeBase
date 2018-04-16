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






Read more:  
https://ss64.com/bash/  
