# Pro Git, Version 2.1.109, 2019-02-04, by Scott Chacon and Ben Straub

Reading: https://github.com/progit/progit2/releases/download/2.1.109/progit.pdf  
Latest version: https://git-scm.com/book/en

# Preface

- Both authors worked/work for Github company

# Getting Started

- Version control is a system (VCS) that records changes to a file or set of files over time so that you can recall specific versions later.  

## About Version Control

### Local Version Control Systems (LVCS)
- Version DB and checkouts on a local computer.
- No more manual copying directories or files, naming `...v1.ext`, `...v2.ext`, etc.
- RCS was first released in 1982 by Walter F. Tichy at Purdue University. It was an alternative tool to the then-popular *Source Code Control System (SCCS)* which was nearly the first version control software tool (developed in 1972 by early Unix developers). RCS works by keeping patch sets (that is, the differences between files) in a special format on disk; it can then re-create what any file looked like at any point in time by adding up all the patches. With RCS, users can make their own revisions of a document, commit changes, and merge them. RCS was originally developed for programs but is also useful for text documents or configuration files that are frequently revised. RCS operates only on single files. It has no way of working with an entire project, so it does not support atomic commits affecting multiple files. Although it provides branching for individual files, the version syntax is cumbersome. Instead of using branches, many teams just use the built-in locking mechanism and work on a single *head branch*. Read more: https://en.wikipedia.org/wiki/Revision_Control_System

### Centralized Version Control Systems (CVCS)
- Version DB on a single server, clients checkout from any computer on a network.
- CVS, Subversion, Perforce, etc. - Centralized Version Control Systems (CVCSs). These have a single server that contains all the versioned files, and a number of clients that check out files from that central place.
- If CVCS (e.g. SVN) server goes down, then during that time nobody can collaborate at all or save versioned changes to anything they’re working on. If the hard disk the central database is on becomes corrupted, and proper backups haven’t been kept, you lose absolutely everything — the entire history of the project except whatever single snapshots people happen to have on their local machines. *Local VCS systems suffer from this same problem.*
- In Perforce, for example, you can’t do much when you aren’t connected to the server; in Subversion and CVS, you can edit files, but you can’t commit changes to your database (because your database is offline).

### Distributed Version Control Systems (DVCS)
- Examples of such systems: Git, Mercurial, Bazaar, Darcs, etc.
- DVCS fully mirror the repository, including its full history. Thus, if any server dies, and these systems were collaborating via that server, any of the client repositories can be copied back up to the server to restore it. Every clone is really a full backup of all the data.
- DVCS deal pretty well with having several remote repositories they can work with, so you can collaborate with different groups of people in different ways simultaneously within the same project. This allows you to set up several types of workflows that aren’t possible in centralized systems, such as hierarchical models.

## A Short History of Git
- Main features of git in comparision to previous Linux kernel source control system BitKeeper: Speed, Simple design, Strong support for non-linear development (thousands of parallel branches), Fully distributed, Able to handle large projects like the Linux kernel efficiently (speed and data size).

## Git Basics
- NOT GIT WAY: Conceptually, most other systems (CVS, Subversion, Perforce, Bazaar, etc.) store information as a list of file-based changes, - this is commonly described as **delta-based** version control. Storing data as changes to a base version of each file.
- !!! **GIT WAY**: Git thinks about its data more like a **stream of snapshots**. Every time you commit, or save the state of your project, **Git basically takes a picture of what all your files look like at that moment** and **stores a reference to that snapshot**. To be efficient, if files have not changed, Git doesn’t store the file again, just a link to the previous identical file it has already stored. This makes Git more like a mini filesystem with some incredibly powerful tools built on top of it.
- Nearly Every Operation Is Local. You have history on your computer. So git is fast, no network overhead.
- Git Has Integrity. Everything in Git is checksummed before it is stored and is then referred to by that checksum. This means it’s impossible to change the contents of any file or directory without Git knowing about it. This functionality is built into Git at the lowest levels and is integral to its philosophy. You can’t lose information in transit or get file corruption without Git being able to detect it.  
- Git uses SHA-1 hash for integrity. This is a 40-character string composed of hexadecimal characters (0–9 and a–f) and calculated based on the contents of a file or directory structure in Git. For example: `24b9da6552252987aa493b52f8696cd6d3b00373`
- !!! In fact, Git stores everything in its database not by file name but by the hash value of its contents.
- !!! **Git Generally Only Adds Data**. It is hard to get the system to do anything that is not undoable or to make it erase data in any way.

### !!! The Three States
- **Committed** means that the data is safely *stored* in your local database.  
-- **TO `.git` DIRECTORY (REPOSITORY)** The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.  
-- "to commit" = "to add from staging area to `.git` directory" 
-- "to checkout" = "to get from `.git` directory to Working tree, in case `.git` directory is local" 
-- "to clone" = "to get from `.git` directory to Working tree, in case `.git` directory is remote"

- **Modified** means that you have *changed* the file but have not committed it to your database yet.  
-- **TO WORKING DIRECTORY (WORKING TREE)**  

- **Staged** means that you have *marked* a modified file in its current version to go into your next commit snapshot.  
-- **TO STAGING AREA** The **staging area is a file**, generally contained in your Git directory, that stores information about what will go into your next commit. Its technical name in Git parlance is the "**index**", but the phrase **"staging area**" works just as well.  
-- "to stage" = "to add from Working tree to Staging area"   
-- "to unstage" = "to get back changes from Satging area to Working tree"

- Working directory (Working tree) -- regular files anyone can work on as usual. The working tree is a **single checkout of one version** of the project. These files are pulled out of the *compressed* database in the Git directory and placed on disk for you to use or modify.

### !!! Basic git workflow
- You modify files in your working tree.
- You selectively stage just those changes you want to be part of your next commit, which adds *only those changes* to the staging area.
- You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.
- If a particular version of a file is in the Git directory, it’s considered committed. If it has been modified and was added to the staging area, it is staged. And if it was changed since it was checked out but has not been staged, it is modified.

## The Command Line
- The command line is the only place you can run all Git commands — most of the GUIs implement only a partial subset of Git functionality for simplicity. Also, while your choice of graphical client is a matter of personal taste, *all users will have the command-line tools installed and available*.  

## Installing Git
- !!! This book was written using Git version 2.8.0.
- Mine was version 2.17.1 (Ubuntu 18.04.01 LTS), even after using `sudo apt install git-all` (adviced method of installation). 
- Mine is version 2.20.1 after installing git from source.

### Installing on Linux
- RPM-based distribution (e.g. RHEL, CentOS, Fedora, etc.): `sudo dnf install git-all`
- Debian-based distribution (e.g. Ubuntu): `sudo apt install git-all`
- Others: http://git-scm.com/download/linux

### Installing on macOS
- One way: install the Xcode Command Line Tools. On Mavericks (10.9) or above you can do this simply by trying to run git from the Terminal the very first time. `git --version`. If you don't have it installed, it will prompt you to install it.
- Another way: Install binary from here: http://git-scm.com/download/mac
- Just another way: GitHub for Mac install. Their GUI Git tool has an option to install command line tools as well. Download here: http://git-scm.com/download/mac 

### Installing on Windows
- One way: The most official build is available for download here: https://git-scm.com/download/win  .Note that this is a project called Git for Windows, which is separate from Git itself!! For more info: https://git-for-windows.github.io/.
- Another way: https://chocolatey.org/packages/git (community maintained project)
- Just another way: https://desktop.github.com/  .The installer includes a command line version of Git as well as the GUI. It also works well with PowerShell, and sets up solid credential caching and sane CRLF settings.

### Installing from source
- You need to have the following libraries that Git depends on: autotools, curl, zlib, openssl, expat, and libiconv.  
    - RPM-based: `sudo dnf install dh-autoreconf curl-devel expat-devel gettext-devel openssl-devel perl-devel zlib-devel`
    - Debian-based: `sudo apt-get install dh-autoreconf libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev`
- In order to be able to add the documentation in various formats (doc, html, info), these additional dependencies are required (Note: users of RHEL and RHEL-derivatives like CentOS and Scientific Linux will have to [enable the EPEL repository](https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F) to download the `docbook2X` package):
    - RPM-based: `sudo dnf install asciidoc xmlto docbook2X`
    - Debian-based: `sudo apt-get install asciidoc xmlto docbook2x`
- Additionally, you also need the `install-info` package:
    - RPM-based: ``
    - Debian-based: `sudo apt-get install install-info`
- Additionally, due to binary name differences:
    - RPM-based: `sudo ln -s /usr/bin/db2x_docbook2texi /usr/bin/docbook2x-texi`
    - Debian-based: ``
- Download the source:
    - From here: https://www.kernel.org/pub/software/scm/git
    - Or from here: https://github.com/git/git/releases
- Then, compile and install:
    - `tar -zxf git-2.0.0.tar.gz`
    - `cd git-2.0.0`
    - `make configure`
    - `./configure --prefix=/usr`
    - `make all doc info`
    - `sudo make install install-doc install-html install-info`
- The test it (get Git via Git itself for updates):
    - `git clone git://git.kernel.org/pub/scm/git/git.git`
    
## First-Time Git Setup
- You should have to do some customization to git config of your machine. These things meant to be done only once on any given computer; they’ll stick around between upgrades. You can also change them at any time by running through the commands again.  
- Linux:
    - !!! `git config`, each level overrides values in the previous level:
        - System: `/etc/gitconfig` <---> `git config --system`
        - System (additional): `$XDG_CONFIG_HOME/git/config` <---> ???
        - User/Global: `~/.gitconfig` or `~/.config/git/config` <---> `git config --global`
        - Project: `.git/config` (in a project) <---> `git config --local` (or simply `git config`)   
        Unsurprisingly, you need to be located somewhere in a Git repository for this (local) option to work properly.
- Windows (need to confirm the order of loading?):
    - System: config file of Git 2.x+ for Windows -- changeable with `git config -f <file>` only:
        - Windows XP: `C:\Documents and Settings\All Users\Application Data\Git\config`.
        - Windows Vista and newer: `C:\ProgramData\Git\config`
    - System: `/etc/gitconfig`, although it’s relative to the MSys root, which is wherever you decide to install Git on your Windows system when you run the installer.
    - User: Git looks for the `.gitconfig` file in the `$HOME` directory (`C:\Users\$USER` for most people)
    - Project: `.git/config` (in a project) <---> `git config --local` (or simply `git config`)
- !!! `git config --list` - check all settings. You may see keys more than once, because Git reads the same key from different files (`/etc/gitconfig` and `~/.gitconfig`, for example). In this case, *Git uses the last value for each unique key* it sees.
- !!! `git config user.name` - check the list of all settings by the key.
- !!!! `git config --show-origin rerere.autoUpdate` - query Git as to the origin for that X value, and it will tell you which configuration file had the final say in setting that X value.

### !!!Your identity
- `git config --global user.name "John Doe"`
- `git config --global user.email johndoe@example.com`
- If you need different details per system user or project then use `--global` (for user) or `--local` (default, for project).

### Your Editor
- !!! The default text editor will be used when Git needs you to type in a message. Use the system one or change it:
    - Linux:
        - `git config --global core.editor emacs` (or use any other you ike, e.g. Vim, Emacs, Notepad++, etc.)
    - Windows:
        - `git config --global core.editor emacs` (provide a full path to the executable file instead of `emacs`), few examples:
            - `git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -nosession"`
            - `git config --global core.editor "'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -nosession"`
- If you don’t setup your editor like this, you may get into a really confusing state when Git attempts to launch an editor. An example on a Windows system may include a prematurely terminated Git operation during a Git initiated edit.

## Getting help
- `git help <verb>`
    - For example, `git help config`
- `man git-<verb>` 
- Freenode IRC server: https://freenode.net/ (#git or #github)
- `-h` or `--help option`, for example: `git config -h`

# Git Basics

## Getting a Git Repository
- You can take a local directory that is currently not under version control, and turn it into a Git repository, or
- You can clone an existing Git repository from elsewhere.

--------
THE REST OF THE CONTENT IS LINUX-ORIENTED
--------

### Initializing a Repository in an Existing Directory
`git init`  
!!! At this point, nothing in your project is tracked yet, the directory "is empty".

`git add *.c` - Add all Working tree files matching pattern `*.c` to Staging area
`git add LICENSE` - Add specific file named `LICENSE` to Staging area
`git commit -m 'initial project version'` - !!! add changes of staging area to `.git` directory (locally), attach a message "initial project version" to the changes.

`git clone` - !!! If you’re familiar with other VCS systems such as Subversion, you’ll notice that the command is "clone" and not "checkout". **This is an important distinction** — instead of getting just a working copy, Git receives a full copy of nearly all data that the server has. Every version of every file for the history of the project is pulled down by default when you run `git clone`.  For example, `git clone https://github.com/libgit2/libgit2`

`git clone https://github.com/libgit2/libgit2`
- creates a directory named `libgit2`
- initializes a `.git` directory inside `libgit2` dir
- pulls down all the data for `https://github.com/libgit2/libgit2` repository
- checks out a working copy of the latest version

If you want to clone the repository into a directory named something other than default repository name, you can specify the new directory name as an additional argument, e.g.:  
`git clone https://github.com/libgit2/libgit2 mylibgit`  
or  
`git clone https://github.com/libgit2/libgit2 .` (note the dot at the end!)


## Recording Changes to the Repository

!!! Each file in your working directory can be in one of two states: **tracked** or **untracked**:  
- **Tracked files** are files that **were in the last snapshot**; they can be *unmodified*, *modified*, or *staged*. In short, tracked files are files that Git knows about.
- **Untracked files** are everything else — any files in your working directory that **were not in your last snapshot** and **are not in your staging area**.

!!! Figure 8. The lifecycle of the status of your files.

### Checking the Status of Your Files

`git status` - which files are in which state, which branch we are on.

*Untracked* basically means that Git sees a file you didn’t have in the previous snapshot (commit); Git won’t start including it in your commit snapshots until you explicitly tell it to do so.

### Tracking New Files

Add file `README` to Staging area:  
`git add README`

!!! If `README` would be a directory, the command `git add ..` would add all the files in that directory recursively.

### Staging Modified Files

**Changes not staged for commit** — which means that a file that is tracked has been modified in the working directory but not yet staged. To stage it, you run the `git add` command. `git add` is a multipurpose command — you use it to begin tracking new files, to stage files, and to do other things like marking merge-conflicted files as resolved.    
!!! **It may be helpful to think** of it more as “add precisely this content to the next commit” rather than “add this file to the project”.  
  
### Short Status

!!! `git status -s` or `git status --short`:  
- `??` - new files that aren't tracked
- `A` - new files that have been added to the staging area
- `M` - modified files
- ...

Left side - Staging area  
Right side - Working tree  

### Ignoring Files

You can create a file listing patterns to match the files you want to ignore, the files is -`.gitignore`  The example of file content:  
```
*.[oa]
*~
```

!!! The rules for the patterns you can put in the .gitignore file are as follows:  
- Blank lines or lines starting with `#` are ignored.
- Standard glob patterns work, and will be applied **recursively** throughout the entire working tree.
- !!!! You can start patterns with a forward slash (`/`) to **avoid recursivity**.
- !!!! You can end patterns with a forward slash (`/`) to specify a **directory**.
- You can **negate a pattern** by starting it with an exclamation point (`!`).


!!!!! Glob patterns are like simplified regular expressions that shells use. An asterisk (`*`) matches zero or more characters; `[abc]` matches any character inside the brackets (in this case a, b, or c); a question mark (`?`) matches a single character; and brackets enclosing characters separated by a hyphen (`[0-9]`) matches any character between them (in this case 0 through 9). You can also use two asterisks to match nested directories; `a/**/z` would match a/z, a/b/z, a/b/c/z, and so on.  

One more example of `.gitignore`:  
```
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

This is a good repository for `.gitignore` kickstart for almost any project:  
https://github.com/sugalvojau/gitignore

It is also possible to have additional `.gitignore` files in subdirectories. The rules in these nested `.gitignore` files apply only to the files under the directory where they are located. (The Linux kernel source repository has 206 .gitignore files.)   


Get help on gitignore: `man gitignore`


### Viewing Your Staged and Unstaged Changes

What have you changed but not yet staged? And what have you staged that you are about to commit?
!!!! That command **compares what is in your working directory with what is in your staging area**. The result tells you the changes you’ve made that you haven’t yet staged.    
So, to see what you’ve changed but not yet staged, type `git diff` with no other arguments:  
`git diff` -- for working directory vs. staging diff


!!!! If you want to see **what you’ve staged that will go into your next commit**. This command compares your staged changes to your last commit.  
`git diff --staged`

!!!!!! `--staged` and `--cached` are synonyms, for example `git --staged` is synonymous to `git --cached`
!!!!!!!!! (...and I was using `git rm -r --cached .` without knowing it is the same as `git rm -r --staged .` . Unbelievable!!!!!!... )


#### !!!! Git Diff in an External Tool
`git difftool` - if you prefer a graphical or external diff viewing program instead of default `git diff`  
`git difftool --tool-help` - see which of existing external programs may be used to see diffs instead of original `git diff`  

For example, adding the following to `.gitconfig` would make `git difftool` command launching PHP Storm:  
```
[diff]
	tool = pstorm
[difftool]
	prompt = false
[difftool.pstorm]
	cmd = /usr/local/bin/pstorm diff "$LOCAL" "$REMOTE"
[merge]
	tool = pstorm
[mergetool.pstorm]
	cmd = /usr/local/bin/pstorm merge "$LOCAL" "$REMOTE" "$BASE" "$MERGED"
```

### Committing Your Changes

`git commit` - doing so launches your editor of choice. This is set by your shell’s `EDITOR` environment variable.  
The default commit message contains the *latest output of the git status command commented* out and one empty line on top.  
When you exit the editor, Git creates your commit with that commit message (with the comments and diff stripped out).  

Use `git config --global core.editor` in order to check which editor is in use.  

`git commit -v` - puts the diff of your change in the editor so you can see exactly what changes you’re committing.    

`git commit -m "Story 182: Fix benchmarks for speed"` - commit with the direct message, no need to open editor anymore.


### Skipping the Staging Area

!!! `git commit -a -m 'added new benchmarks'` - automatically stage every file that is already tracked before doing the commit, letting you skip the `git add` part.  
`-a` flag includes all changed files. This is convenient, **but be careful**; sometimes this flag will cause you to include unwanted changes.

### Removing Files
  
!!!! If you simply remove the file from your working directory, it shows up under the “Changes not staged for commit” (that is, **unstaged**) area of your git status output.  

!!!!! `git rm` - remove the file from staging area **and working directory**. **This command stages the file’s removal**.  
The next time you commit, the file will be gone and no longer tracked. If you modified the file or had already added it to the staging area, you must force the removal with the `-f` option.  

!!!!!! `git rm --cached README` - keep the file in your working tree but remove it from your staging area.    
!!! This is particularly useful if you forgot to add something to your `.gitignore` file and accidentally staged it, like a large log file or a bunch of `.a` compiled files.  

You can pass files, directories, and file-glob patterns, for example:    
`git rm log/\*.log`    
!!!!!??? Note the backslash (`\`) in front of the `*`. This is necessary because Git does its own filename expansion in addition to your shell’s filename expansion. This command removes all files that have the `.log` extension in the `log/` directory.  


### Moving Files

!!! Unlike many other VCS systems, Git doesn’t explicitly track file movement. If you rename a file in Git, no metadata is stored in Git that tells it you renamed the file. However, Git is pretty smart about figuring that out after the fact.  

`git mv file_from file_to` - to rename the file.  
!!!! which is actually equivalent to this:  
```
mv README.md README
git rm README.md
git add README
```

!!!! **The only real difference is that `git mv` is one command instead of three** — it’s a convenience function. More importantly, you can use any tool you like to rename a file, and address the `add`/`rm` later, before you commit.  

## Viewing the Commit History

`git log` - history by date DESC  
  
`git log --patch` - shows the difference (the patch output) introduced in each commit. You may use `-p` instead of `--patch`.  
  
`git log -2` - shows two last history items, use any number.  
  
`git log --stat` - abbreviated stats for each commit. Prints below each commit entry a list of modified files, how many files were changed, and how many lines in those files were added and removed.  
  
!!!!! `git log --pretty=oneline` - changes the log output to formats other than the default. The `oneline` option prints each commit on a single line, which is useful if you’re looking at a lot of commits.
`git log --pretty=short` - ...  
`git log --pretty=full` - ...  
`git log --pretty=fuller` - ...  

!!!!! `git log --pretty=format:"%h - %an, %ar : %s"` - the `format` option allows to specify own format. **This is especially useful when you’re generating output for machine parsing** — because you specify the format explicitly, you know it won’t change with updates to Git.  
This outputs lines like this:  
`a16d814c - FirstName LastName, 7 days ago : Commit message is shown here`  

See `git help log` for more information on formats available, etc.  

!!!! **What is the difference between author and committer?**  
The **author** is the person who originally wrote the work,  
whereas the **committer** is the person who last applied the work.  
So, if you send in a patch to a project and one of the core members applies the patch, both of you get credit — you as the author, and the core member as the committer.  

!!! `git log --pretty=format:"%h %s" --graph` -- with `--graph` you see the tree of changes.  

!!! `git log --since=2.weeks` - show log since some date, may be also "2008-01-15", "2 years 1 day 3 minutes ago", etc.  

!!!! `git log --grep somekeywordsorso` - search for keywords in the commit messages.  

You can specify more than one instance of both the `--author` and `--grep` search criteria, which will limit the commit output to commits that match any of the `--author` patterns and any of the `--grep` patterns; 
however, adding the `--all-match` option further limits the output to just those commits that match all `--grep` patterns.  

!!!! `git log -S function_name` (for example: `git log -S findById`) - if you wanted to find the last commit that added or removed a reference to a specific function.  
It is (`-S` option) colloquially referred to as **Git’s “pickaxe” option**.    
which takes a string and shows only those commits that changed the number of occurrences of that string.  

!!!!! `git log fileordirname` - chows shanges of the directory or file.  

Some useful options: `-<n>`, `--since`, `--after`, `--until`, `--before`, `--author`, `--committer`, `--grep`, `-S`  
Fo example: `git log --pretty="%h - %s" --author='Name Surname' --since="2008-10-01" --before="2019-02-01" --no-merges -- var/`  


## Undoing Things  

`git commit --amend` - This command takes your staging area and uses it for the commit. 
If you’ve made no changes since your last commit (for instance, you run this command immediately after your previous commit), 
then your snapshot will look exactly the same, and all you’ll change is your commit message.  



...


 
    



