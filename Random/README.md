# 2KB.txt
---------

sudo apt install mysql-client
mysql -V
sudo apt install mysql-server
sudo mysql_secure_installation (root|root)
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf (and change `bind-address = 127.0.0.1` to `bind-address = 0.0.0.0`) ,- in case we wish to connect to our MySQL server remotely using MySQL client.
sudo service mysql restart





`sudo apt-get install gparted gpart`
`sudo apt install id-utils` (for `gid` and `uid` to work)


**Explain: `sudo -i`**  
Read more:  
https://unix.stackexchange.com/questions/176997/sudo-as-another-user-with-their-environment  

**Explain: `sudo -i -u user`**  
Read more:  
https://unix.stackexchange.com/questions/176997/sudo-as-another-user-with-their-environment  

**Explain: `sudo -i -u user whoami`**  
Read more:  
https://unix.stackexchange.com/questions/176997/sudo-as-another-user-with-their-environment  

**Explain: `sudo -i -u user echo \$HOME`**  
Read more:  
https://unix.stackexchange.com/questions/176997/sudo-as-another-user-with-their-environment  

**Explain: `sudo -S -u mysql ls /media/paulius/853e343c-a7d6-4569-9082-0281013caf1b/mysql/datadir`**
Read more:  
https://unix.stackexchange.com/questions/176997/sudo-as-another-user-with-their-environment

**Explain: `sudo mkfs.ext4 /dev/sda1`**  
Read more:  
https://unix.stackexchange.com/questions/315063/mount-wrong-fs-type-bad-option-bad-superblock/315070  

**Explain: `mount -t vfat -o umask=0022,gid=33,uid=33 dev /var/www` (may not work sometimes)**  
Read more:  
https://unix.stackexchange.com/questions/30268/mount-device-with-r-w-access-to-specific-user  
https://askubuntu.com/questions/44542/what-is-umask-and-how-does-it-work  

**Explain: `getent passwd`**  
Lists all users.
Read more:  
https://serverfault.com/questions/355292/show-all-users-and-their-groups-vice-versa  

**Explain: `getent group`**  
Lists all groups.
Read more:  
https://serverfault.com/questions/355292/show-all-users-and-their-groups-vice-versa  

**Explain: `getent group | grep username`**  
Lists all groups with a specific user.
Read more:  
https://serverfault.com/questions/355292/show-all-users-and-their-groups-vice-versa  

**What is `/etc/fstab` file for?**

**What is AppArmor for?**  

**Explain `sudo rsync -av /var/lib/mysql /mnt/volume-nyc1-01`**  

**Explain `sudo nano /etc/apparmor.d/tunables/alias`. What is the `alias` file for?**  

`sudo nano /etc/apparmor.d/usr.sbin.mysqld`

**What is a loop device on Linux?**  
Read more:
https://askubuntu.com/questions/906581/what-is-dev-loopx

**Explain `/sbin/losetup --list`**
Finding which images belong to which /dev/loop

`sudo fdisk -l`
List all disks?

`sudo mount -t auto -v /dev/sdb1 /mnt/mount_name`
Mounts auto guesing file system, -v is for verbosity

What is UNIX auth_socket plugin used by MySQL on Ubuntu 18.04?
https://dev.mysql.com/doc/refman/5.7/en/socket-pluggable-authentication.html

Explain the result, especially the "plugin" part:
Connect to MySQL with root: sudo mysql -u root
USE mysql;
SELECT User, Host, plugin FROM mysql.user;
, - Finding out which auth plugin is being used to connect to MySQL with user X? 
, - https://stackoverflow.com/questions/39281594/error-1698-28000-access-denied-for-user-rootlocalhost/42742610#42742610

Explain:
sudo mysql -u root # I had to use "sudo" since is new installation
USE mysql;
UPDATE user SET plugin='mysql_native_password' WHERE User='root';
FLUSH PRIVILEGES;
exit;
service mysql restart
,-- set the root user to use the `mysql_native_password` plugin, https://stackoverflow.com/questions/39281594/error-1698-28000-access-denied-for-user-rootlocalhost/42742610#42742610

Explain:
sudo mysql -u root # I had to use "sudo" since is new installation
USE mysql;
CREATE USER 'YOUR_SYSTEM_USER'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON *.* TO 'YOUR_SYSTEM_USER'@'localhost';
UPDATE user SET plugin='auth_socket' WHERE User='YOUR_SYSTEM_USER';
FLUSH PRIVILEGES;
exit;
service mysql restart
, -- create a new db_user with you system_user
, -- https://stackoverflow.com/questions/39281594/error-1698-28000-access-denied-for-user-rootlocalhost/42742610#42742610

What is the difference between `auth_socket` and `unix_socket`?
On some systems (e.g., Debian stretch) 'auth_socket' plugin is called 'unix_socket', so the corresponding SQL command should be: UPDATE user SET plugin='unix_socket' WHERE User='YOUR_SYSTEM_USER';
https://stackoverflow.com/questions/39281594/error-1698-28000-access-denied-for-user-rootlocalhost/42742610#42742610


mysql -u username -p database_name < file.sql
-R and --triggers to keep the routines and triggers of original database


"You probably have two disks called “sda” and “sdb”, there will also be some called “sda1” and maybe “sda2” these are partitions, the ones without numbers are the disk’s", - http://dev-random.net/mysql-data-on-secondary-hard-disk/

https://linuxexpresso.wordpress.com/2010/03/14/mount-partitions-in-terminal-fstab/
https://linuxconfig.org/install-mysql-on-ubuntu-18-04-bionic-beaver-linux
https://devanswers.co/ubuntu-18-04-initial-server-setup/

apt list --installed

Explain: 
sudo mysqladmin -p -u root version

Explain:
grep --color --text -inr  'INSERT INTO `User` VALUES (1121' inriver-mysql-db.sql

Explain:
sed -n '12384715,12384724p' inriver-mysql-db.sql > tables/sysdiagrams.sql

Explain:
wc -l inriver-mysql-db.sql 
Output:
12384724 inriver-mysql-db.sql

Explain:
sed 's/\x0/ /g' file1 > file2
Removes null bytes by replacing them to space characters
https://superuser.com/questions/287997/how-to-use-sed-to-remove-null-bytes

MySQL explain:
SHOW VARIABLES LIKE "secure_file_priv";
https://stackoverflow.com/questions/32737478/how-should-i-tackle-secure-file-priv-in-mysql

Explain:
dpkg -S /etc/apparmor.d/usr.sbin.mysqld

Explain:
dpkg -S `which zgrep`

Explain:
apt-file search nvcc

Explain:
sudo aa-status

Explain:
sudo ln -s /etc/apparmor.d/usr.sbin.mysqld /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.sbin.mysqld
sudo aa-status
sudo rm /etc/apparmor.d/disable/usr.sbin.mysqld
sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld
sudo aa-status

- Does `cp` command override the destination file if such already exists?
???

Explain:
first="I love Suzy and Mary"
second="Sara"
first=${first/Suzy/$second}

Explain:
first="Suzy, Suzy, Suzy"
second="Sara"
first=${first//Suzy/$second}
# first is now "Sara, Sara, Sara"
Read more: https://stackoverflow.com/questions/13210880/replace-one-substring-for-another-string-in-shell-script

What is the difference between `first=${first/Suzy/$second}` and `first=${first//Suzy/$second}` (explain the single and double slash part only)? 
Read more:
https://stackoverflow.com/questions/13210880/replace-one-substring-for-another-string-in-shell-script


Explain:
The test command ([ here): 
http://man7.org/linux/man-pages/man1/test.1.html
https://stackoverflow.com/questions/638975/how-do-i-tell-if-a-regular-file-does-not-exist-in-bash

Explain
https://unix.stackexchange.com/questions/258341/echo-a-string-with-a-variable-in-it-without-expanding-evaluating-it
https://ryanstutorials.net/bash-scripting-tutorial/bash-if-statements.php
https://stackoverflow.com/questions/525592/find-and-replace-inside-a-text-file-from-a-bash-command
https://stackoverflow.com/questions/13210880/replace-one-substring-for-another-string-in-shell-script
https://stackoverflow.com/questions/638975/how-do-i-tell-if-a-regular-file-does-not-exist-in-bash
https://stackoverflow.com/questions/2990414/echo-that-outputs-to-stderr
https://stackoverflow.com/questions/592620/how-to-check-if-a-program-exists-from-a-bash-script
https://stackoverflow.com/questions/11287861/how-to-check-if-a-file-contains-a-specific-string-using-bash
https://stackoverflow.com/questions/4381618/exit-a-script-on-error
https://stackoverflow.com/questions/19306771/get-current-users-username-in-bash

Explain:
https://codeburst.io/the-2018-web-developer-roadmap-826b1b806e8d

How PEAR (http://pear.php.net/) and PECL (https://pecl.php.net/) differ?
PEAR is a framework and distribution system for reusable PHP components. PECL is a repository for PHP Extensions. PECL contains C extensions for compiling into PHP. As C programs, PECL extensions run more efficiently than PEAR packages. PEARs and PECLs use the same packaging and distribution system. As such this resource is clever enough to abstract away the small differences and can be used for managing either. This resource also creates the proper module .ini file for each PECL extension at the correct location for each supported platform.  
Read more:  
http://pear.php.net/  
https://pecl.php.net/  

What's the difference between git clone --mirror and git clone --bare?
https://stackoverflow.com/questions/3959924/whats-the-difference-between-git-clone-mirror-and-git-clone-bare


Explain:
```
if [ $? -eq 0 ]; then
    echo "Executed successfully."
else
    echo "Failed. Stopping build process."
    exit 1
fi
```

What is the difference between ``




mysqld --help --verbose
tail /var/log/mysql/error.log -f
/media/paulius/853e343c-a7d6-4569-9082-0281013caf1b/mysql

sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf					<-- check where is the datadir set now
sudo rsync -av /var/lib/mysql /mnt/hdd1tb/mysql/datadir			<-- copy files fromCurrentDatadir toNewDatadir
sudo ls -al /mnt/hdd1tb/mysql/datadir/mysql						<-- make sure it has been copied
sudo -S -u mysql ls /mnt/hdd1tb/mysql/datadir/mysql/			<-- test if mysql can reach the new directory
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf					<-- check if datadir is set to be the new dir correctly
  # comment the old line starting "datadir = "...				
  datadir = /mnt/hdd1tb/mysql/datadir/mysql
sudo nano /etc/apparmor.d/usr.sbin.mysqld						<-- allow mysqld to use the new directory
  # Allow data_dir (extra hdd) access
  /mnt/hdd1tb/mysql/datadir/mysql/ r,
  /mnt/hdd1tb/mysql/datadir/mysql/** rwk,
sudo service apparmor reload 
sudo service mysql restart
If errors:
	tail /var/log/mysql/error.log -f




update user set authentication_string=password('YOURSUPERSECRETPASSWORD') where user='root';
flush privileges;
quit;

Remove:
sudo apt-get remove --purge mysql-server mysql-client mysql-common
sudo apt-get autoremove
sudo apt-get autoclean


sudo rm -rf /var/lib/mysql
sudo rm -rf /var/run/mysqld


sudo apt update && sudo apt install mysql-server
sudo service mysql status
q
sudo mysql




https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04
https://coderwall.com/p/j9btlg/reset-the-mysql-5-7-root-password-in-ubuntu-16-04-lts
https://www.techandme.se/reset-mysql-5-7-root-password/


Install MySQL on Ubuntu 18.04:

sudo apt install mysql-client
mysql -V
sudo apt install mysql-server
before going live: sudo mysql_secure_installation





/dev/sda



/dev/sda1 /mnt/hdd1tb ext4 defaults 0 0
/dev/sda1       /mnt/hdd1tb     ext4    defaults,uid=1000,umask=0 0 0



What is the difference between Typewriter and Teletype devices?
https://en.wikipedia.org/wiki/Mainframe_computer

What is a mainframe computer?

Do anybody produces mainframe computers now (year of 2018)?  

What is Linux kernel?

What is linux distribution?
Linux consists of a kernel, which is the core control software, and many libraries and utilities that relay on the kernel to provide features with which users interact. The OS is available in many different distributions, which are collections of a specific kernel with specific support programs?



# 3KB.txt
---------

What are simmilaritries and differences between NPM (Node Package Manager) and Yarn?
Similarities:
- Both solve exact same problem - package management
- package.json (`npm init`) 

Differences:
- Yarn is a superset of NPM (uses NPM's registry as backend)
- Yarn installs packages in parallel while NPM - sequentially.


What package managers for what languages do you know?
- PHP: Composer (composer.json + composer.lock)
- Python: Pypi
- Java: Gradle
- Javascript: NPM, Yarn (package.json + yarn.lock), Webpack (webpack.config.js)


- What is the difference between ES6 and ES2015?
It is the same.
https://medium.com/front-end-hacking/what-are-npm-yarn-babel-and-webpack-and-how-to-properly-use-them-d835a758f987

What is Babel for?
Babel is a JS transpiler that converts new JS code into old ones. For example, one can easily add presets such as es2015, es2016, es2017, so that Babel compiles them to ES5.
https://medium.com/front-end-hacking/what-are-npm-yarn-babel-and-webpack-and-how-to-properly-use-them-d835a758f987

- What is PostCSS?

Webpack is a modular build tool that has two sets of functionality — Loaders and Plugins. Loaders transform the source code of a module. For example, style-loader adds CSS to DOM using style tags. sass-loader compiles SASS files to CSS. babel-loader transpiles JS code given the presets. Plugins are the core of Webpack. They can do things that loaders can’t. For example, there is a plugin called UglifyJS that minifies and uglifies the output of webpack.

- What is Ext JS?
https://en.wikipedia.org/wiki/Ext_JS



Docker:
Explain the follining content found in `Dockerfile`:
```
FROM node:9.11.2-alpine
WORKDIR /srv/pim/
USER root
CMD while sleep 3600; do :; done
```


# oauth2.txt
------------

Client-server:
Whether a computer is a client, a server, or both, is determined by the nature of the application that requires the service functions. For example, a single computer can run web server and file server software at the same time to serve different data to clients making different kinds of requests. Client software can also communicate with server software within the same computer.

Communication between servers, such as to synchronize data, is sometimes called inter-server or server-to-server communication.

Clients and servers exchange messages in a request–response messaging pattern.
Request–response is a message exchange pattern in which a requestor sends a request message to a replier system which receives and processes the request, ultimately returning a message in response. This is a simple, but powerful messaging pattern which allows two applications to have a two-way conversation with one another over a channel.










- What are the main problems and limitations related to a third-party application accessing the access-restricted resource (protected resource) on the server via HTTP?
 - Third-party applications are required to store the resource owner’s credentials for future use, typically a password in clear-text.
 - Servers are required to support password authentication, despite the security weaknesses inherent in passwords. 
 - Third-party applications gain overly broad access to the resource owner’s protected resources, leaving resource owners without any ability to restrict duration or access to a limited subset of resources.
 - Resource owners cannot revoke access to an individual third party without revoking access to all third parties, and must do so by changing the third party’s password.
 - Compromise of any third-party application results in compromise of the end-user’s password and all of the data protected by that password.
 
 
 - introducing an authorization layer and separating the role of the client from that of the resource owner
 
 - Instead of using the resource owner’s credentials to access protected resources, the client obtains an access token
 
 - The use of OAuth over any protocol other than HTTP is out of scope (of RFC 6749).
 
 - The OAuth 2.0 protocol is not backward compatible with OAuth 1.0.
 
 - The two versions may co-exist on the network, and implementations may choose to support both.
 
 - What is resource owner in OAuth2.0?
 An entity capable of granting access to a protected resource. 
 When the resource owner is a person, it is referred to as an end-user.
 
 - What is resource server in OAuth2.0?
The server hosting the protected resources, capable of accepting and responding to protected resource requests using access tokens.

- What is client in OAuth2.0?
An application making protected resource requests on behalf of the resource owner and with its authorization.  The term "client" does not imply any particular implementation characteristics (e.g., whether the application executes on a server, a desktop, or other devices).

- What is authorization server in OAuth2.0?
The server issuing access tokens to the client after successfully authenticating the resource owner and obtaining authorization.


- The authorization server may be the same server as the resource server or a separate entity.

- A single authorization server may issue access tokens accepted by multiple resource servers.


     +--------+                               +---------------+
     |        |--(A)- Authorization Request ->|   Resource    |
     |        |                               |     Owner     |
     |        |<-(B)-- Authorization Grant ---|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(C)-- Authorization Grant -->| Authorization |
     | Client |                               |     Server    |
     |        |<-(D)----- Access Token -------|               |
     |        |                               +---------------+
     |        |
     |        |                               +---------------+
     |        |--(E)----- Access Token ------>|    Resource   |
     |        |                               |     Server    |
     |        |<-(F)--- Protected Resource ---|               |
     +--------+                               +---------------+
	 

- (A) request can be made directly to the resource owner (as shown), or preferably indirectly via the authorization server as an intermediary.

- (B) The client receives an authorization grant, expressed using **one of four grant types** (-- authorization code, implicit, resource owner password credentials, and client credentials --) defined in the OAuth2.0 specification **or using an extension grant type**. The authorization grant type depends on the method used by the client to request authorization and the types supported by the authorization server.

- 

 
 
 
 