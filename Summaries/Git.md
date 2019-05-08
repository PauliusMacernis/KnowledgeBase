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


## !!!!!! Undoing Things  

!!!!!! `git commit --amend` - Fix the last commit (fix commit message, files added). Which means - you will be modifying the last snapshot in `.git` directory.  (??)  
This command takes your staging area and uses it for the commit. 
If you’ve made no changes since your last commit (for instance, you run this command immediately after your previous commit), 
then your snapshot will look exactly the same, and all you’ll change is your commit message.  

!!!!! **It’s important to understand that when you’re amending your last commit, you’re not so much fixing it as replacing it entirely with a new, improved commit** that pushes the old commit out of the way and puts the new commit in its place.
Effectively, it’s as if the previous commit never happened, and it won’t show up in your repository history.
The obvious value to amending commits is to make minor improvements to your last commit, without cluttering your repository history with commit messages of the form, “Oops, forgot to add a file” or “Darn, fixing a typo in last commit”.  


### Unstaging a Staged File

!!!!! `git reset HEAD CONTRIBUTING.md` - to unstage the file. Physical file in the working directory is not touched.  

!!!!! Physical file is not being touched with `git reset ...`. However, adding `--hard` flag would change the situation. Be careful!!!


### Unmodifying a Modified File

!!!! `git checkout -- CONTRIBUTING.md` - when we realize that we don’t want to keep our changes to the `CONTRIBUTING.md` file. This is how can we easily unmodify it — revert it back to what it looked like when we last committed (or initially cloned, or however we got it into our working directory).  
!!!! It’s **important to understand** that `git checkout -- <file>` is a dangerous command. **Any changes you made to that file are gone** — Git just copied another file over it. Don’t ever use this command unless you absolutely know that you don’t want the file.  

!!!!!!!! Remember, anything that is committed in Git can almost always be recovered. However, anything you lose that was never committed is likely never to be seen again.  

## Working with Remotes  

Remote repositories are versions of your project that are hosted on the Internet or network somewhere. You can have several of them, each of which generally is either read-only or read/write for you.  
It is entirely possible that you can be working with a “remote” repository that is, in fact, on the same host you are. 
The word “remote” does not necessarily imply that the repository is somewhere else on the network or Internet, only that it is elsewhere. Working with such a remote repository would still involve all the standard pushing, pulling and fetching operations as with any other remote.  

### Showing Your Remotes  

`git remote` - lists the shortnames of each remote handle you’ve specified. `origin` is default name Git gives to the server cloned from.  

`git remote -v` - list remotes with URLs.  

### Adding Remote Repositories

`git remote add <shortname> <url>` - add a new remote repository, for example: `git remote add pb https://github.com/paulboone/ticgit`

`git fetch remoterepositoryshortname` - fetch all the information that `repositoryshortname` has but that you don’t yet have in your repository.  
!!!! The command goes out to that remote project and **pulls down all the data from that remote project** that you don’t have yet. 
After you do this, you should have **references to all the branches from that remote, which you can merge in or inspect** at any time.  

!!!! **It’s important to note that the git fetch command only downloads the data to your local repository — it doesn’t automatically merge it with any of your work or modify what you’re currently working on.** 
You have to merge it manually into your work when you’re ready.  

!!!!!!! **IF your current branch is set up to track a remote branch** THEN you **can use the git pull** command to **automatically fetch and then merge** that **remote branch into your current branch**.  

!!!! **by default, the git clone command automatically sets up your local master branch to track the remote master branch (or whatever the default branch is called) on the server you cloned from.**  

!!!! Running `git pull` generally **fetches data** from the server you originally cloned from and **automatically tries to merge it into the code you’re currently working on**.  

### Pushing to Your Remotes

!!! `git push <remote> <branch>` - push your `<branch>` (e.g. `master`) branch to your **`<remote>`** (e.g. `origin`) server.  
This command works only if you cloned from a server to which you have write access and if nobody has pushed in the meantime.    
If you and someone else clone at the same time and they push upstream and then you push upstream, your push will rightly be rejected.  
You’ll have to fetch their work first and incorporate it into yours before you’ll be allowed to push.  

### Inspecting a Remote

!!! `git remote show <remote>` - lists the URL for the remote repository, tracking branch info, etc.


### Renaming and Removing Remotes  

`git remote rename <fromremotename> <toremotename>` - change a remote’s shortname from one (e.g. `meat`) to another (e.g. `visma`).  
It’s worth mentioning that this changes all your remote-tracking branch names, too. What used to be referenced at `<fromremotename>/master` (e.g. `meat/master`) is now at `<toremotename>/master` (e.g. `visma/master`).

`git remote remove <remotename>` or `git remote rm <remotename>` - remove a remote  
!!! Once you delete the reference to a remote this way, **all remote-tracking branches and configuration settings** associated with that remote are also deleted.  


## Tagging

`git tag` or `git tag -l` or `git tag --list` - list all tags in alphabetical order; the order in which they appear has no real importance.  

`git tag -l "v1.8.*"` - search for tags that match a particular pattern (e.g. for `v1.8.anything` tags)  

**Listing tag wildcards requires `-l` or `--list` option.**    
If you want just the entire list of tags, running the command `git tag` implicitly assumes you want a listing and provides one; the use of `-l` or `--list` in this case is optional.  

### Creating Tags

Git supports two types of tags:  
- lightweight - a pointer to a specific commit.
- annotated - stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). It is recommended way of tagging most of the times. But not always, of course.  

### Annotated Tags

`git tag -a v1.4 -m "my version 1.4"` - creating  
`-m` specifies a tagging message, which is stored with the tag.  

`git show v1.4` - shows the tag data along with the commit that was tagged  

### Lightweight Tags  

`git tag v1.4` - creating (don’t supply any of the `-a`, `-s`, or `-m` options, just provide a tag name)  

### Tagging Later  

`git tag -a v1.2 9fceb02`

### !!! Sharing Tags

!!!! `git push origin <tagname>` - **By default, the git push command doesn’t transfer tags to remote servers** . 
You will have to **explicitly push tags** to a shared server after you have created them. 
This process is just like sharing remote branches — you can run `git push origin <tagname>`
  
!!!! `git push origin --tags` - **If you have a lot of tags that you want to push up at once**, you can also use the **`--tags`** option to the `git push` command. This will transfer all of your tags to the remote server that are not already there.  

### Deleting Tags

`git tag -d <tagname>` - this removes the tag from **local** repo.
`git push <remote> :refs/tags/<tagname>` - this will push local tag update to **remote** repo.  

### Checking out Tags

`git checkout <tag>` (e.g. `git checkout 2.0.0`) - If you want to view the versions of files a tag is pointing to, you can do a git checkout, though this puts your repository in “**detached HEAD**” state, which has some ill side effects.  
  In “detached HEAD” state, if you make changes and then create a commit, the tag will stay the same, but your new commit won’t belong to any branch and will be unreachable, except by the exact commit hash. 
  Thus, if you need to make changes — say you’re fixing a bug on an older version, for instance — you will generally want to create a branch, e.g. `git checkout -b version2 v2.0.0`. If you do this and make a commit, 
  your `version2` branch will be slightly different than your `v2.0.0` tag since it will move forward with your new changes, so **do be careful**.  
  
## Git Aliases
  
  !!!! Set up an alias for each command using `git config`, for example `git config --global alias ci commit`. This means that, for example, instead of typing `git commit`, you just need to type `git ci`.  
  
  !!! This technique can also be very useful in creating commands that you think should exist. For example, to correct the usability problem you encountered with unstaging a file, you can add your own unstage alias to Git:
  `git config --global alias.unstage 'reset HEAD --'`
  `git config --global alias.last 'log -1 HEAD'`
  
  !!!!!!! **Run an external command, rather than a Git subcommand. In that case, you start the command with a `!` character.**. For example:
  `git config --global alias.visual '!gitk'`
  
  
  
# Git branching
  
  Branching means you diverge from the main line of development and continue to do work without messing with that main line.
  
## Branches in a Nutshell
  
  !!!! When you make a commit, *Git stores a commit object that contains*: 
  - the author’s name 
  - the author's email address, 
  - the typed message, 
  - a pointer to the snapshot of the staged content
  - pointers to the commit or commits that directly came before this commit (its parent or parents): 
    - *zero parents for the initial commit*, 
    - *one parent for a normal commit*, and 
    - *multiple parents for a commit that results from a merge* of two or more branches.
  
  !!!! Let’s assume that you have a directory containing three files, and you stage them all and commit. 
  - When you stage the files (e.g. 3) then git:
    - computes a checksum for each file (the SHA-1 hash), 
    - stores that version of the file in the Git repository (Git refers to them as `blobs`), and 
    - adds that checksum to the staging area
  - When you create the commit by running `git commit`, 
    - Git checksums each subdirectory (in this case, just the root project directory) and 
    - stores those tree objects in the Git repository. 
    - Git then creates a commit object that has the metadata and a pointer to the root project tree so it can re-create that snapshot when needed.
  - At the end you have 5 objects in the git repository:
    - 3x **blobs** (each representing the contents of one of the 3 files)
    - 1x **tree** that lists the contents of the directory and specifies which file names are stored as which blobs
    - 1x **commit with the pointer to that root tree** and all the commit metadata  (author name and email, message, pointer to the snapshot of the staged content, pointers to the commit or commits that directly came before this commit (its parent or parents)).

  !!!!! Figure 9. A commit and it's tree  
  !!!!! Figure 10. Commits and their parents  
  
  !!!!!! A **branch** in Git is simply a lightweight **movable pointer to one of these commits**. The default branch name in Git is master. As you start making commits, you’re given a `master` branch that points to the last commit you made.  
  **Every time you commit, the `master` branch pointer moves forward automatically**.
  
  !!! The **`master` branch in Git is not a special branch**. It is exactly like any other branch. The only reason nearly every repository has one is that the `git init` command creates it by default and most people don’t bother to change it.  
  
  !!!!!! (COMMIT > SNAPSHOT > TREE > BLOB)  
  See figures 9-12 for more ihfo.  
  
  
### Creating a New Branch

  !!! New branch = new pointer to move around (within snapshots?)  
  
  `git branch testing` , - this creates a new pointer (called `testing`) to the same commit you’re currently on. 
  The `git branch` command** only created a new branch — it didn’t switch** to that branch.
  
  
  !!!!!! **How does Git know what branch you’re currently on?**  
  **It keeps a special pointer called `HEAD`.**  
  In Git, this is a pointer to the **local branch you’re currently on**.  
  
  
  !!!!!!! (HEAD > BRANCH > COMMIT > SNAPSHOT > TREE > BLOB)
  
  `git log` - shows where the branch pointers are pointing, where is the `HEAD` pointer pointing to. This option is called `--decorate`. For example:    
  - `git log --decorate` or in a compact view:
  - `git log --oneline --decorate`
  
### Switching Branches

  !!!!!! `git checkout <branch>` 
  1) moves `HEAD` to point to another branch (aka "switching to another branch"), and 
  2) reverts the files in the working directory back to the snapshot that <branch> points to.
  
  !!! It’s **important to note** that when you switch branches in Git, files in your working directory will change.  
  If you switch to an older branch, your working directory will be reverted to look like it did the last time you committed on that branch.  
  Git adds, removes, and modifies files automatically to make sure your working copy is what the branch looked like on the last commit to it.  
  **If Git cannot do it cleanly, it will not let you switch at all**.  
  
  `git log --oneline --decorate --graph --all` - check for the history, including divergent history.
  (Divergent history - when the history is not in a one solid row, e.g. in a branches that are changed with the new features other branches don't know about yet)?
  
  A **branch in Git is actually a simple file that contains the 40 character** SHA-1 checksum of the commit it points to.  
  Creating a new branch is as quick and simple as writing 41 bytes to a file (40 characters and a newline).  
  
  
## Basic Branching and Merging


### Basic Branching

  `git checkout -b <branch>` - create a new branch and switch to it at the same time. This is shorthand for `git branch <branch>` and `git checkout <branch>`

  Before you do switch branches, note that if your working directory or staging area has uncommitted changes that conflict with the branch you’re checking out, Git won’t let you switch branches. It’s best to have a clean working state when you switch branches.  
  
  Merging `<branch>` into `master` (or any other branch):  
  `git checkout master`  
  `git merge <branch>`  
  
  !!**"fast-forward merge"** - Git simply moves the pointer forward.   
   To phrase that another way, when you try to merge one commit with a commit that can be reached by following the first commit’s history, Git simplifies things by moving the pointer forward because there is no divergent work to merge together — this is called a "fast-forward".  
  
  !!!! `git branch -d <branch>` - delete the branch. For example, because another branch (e.g. `master`) points to the same (or newer) snapshot. Or because the changes in the branch is irrelevantly old and you are sure the old branch is not needed anymore.
  
### Basic Merging

  !!!!!!**"Merge made by the 'recursive' strategy."** - In this case, your development history has diverged from some older point.  
  Because the commit on the branch you’re on isn’t a direct ancestor of the branch you’re merging in, Git has to do some work.  
  In this case, Git does a simple **three-way merge, using the two snapshots pointed to by the branch tips and the common ancestor of the two**.  
  (see figure 24)  
  Instead of just moving the branch pointer forward, Git creates a new snapshot that results from this three-way merge and automatically creates a new commit that points to it.  
  (see figure 25)  
  __**This is referred to as a merge commit, and is special in that it has more than one parent.**__
  
### Basic Merge Conflicts
  
  If you changed the same part of the same file differently in the two branches you’re merging, Git won’t be able to merge them cleanly, you'll get a merge conflict.  
  !!!!!! And git is not creating merge commit in the case of conflict. It has paused the process while you resolve the conflict.  
  Use `git status` to find files failing to be merged (aka. "unmerged paths").  
  Anything that has merge conflicts and hasn’t been resolved is listed as unmerged. Git adds standard conflict-resolution markers to the files that have conflicts, so you can open them manually and resolve those conflicts.  
  **After you’ve resolved each of these sections in each conflicted file, run `git add` on each file to mark it as resolved. Staging the file marks it as resolved in Git.**  
  
  `git mergetool` - in case you prefer graphical tool to resolve conflicts. In this case, git setting `merge.tool` will matter, or you will have to pick the tool when using the command. After you exit the merge tool, Git asks you if the merge was successful. If you tell the script that it was, it stages the file to mark it as resolved for you. You can run `git status` again to verify that all conflicts have been resolved. If you’re happy with that, and you verify that everything that had conflicts has been staged, you can type `git commit` to finalize the merge commit. The default commit message will be generated in, but you may change it if you will.  
  
## Branch Management  

  !!!!! `git branch` - list of current branches. `*` in the list marks the branch that `HEAD` points to.  
  
  !!! `git branch -v` - list of current branches, where `HEAD` points to, and **the last commit message**.
  
  !!!!!!!!! `git branch --merged` or `git branch --merged <branch>` - to see which branches are already merged into the branch you’re on.  
  Branches on this list without the `*` in front of them are generally fine to delete with `git branch -d`; you’ve already incorporated their work into another branch, so you’re not going to lose anything.  
  
  !!!!!!!!! `git branch --no-merged` or `git branch --no-merged <branch>` - to see which branches are NOT MERGED into the branch you’re on.   
  Deleting branches under this list will not work if you use `git branch -d <branch>`. You will get the error and be asked to use `git branch -D <branch>` instead.  
  
  
## Branching Workflows

### Long-Running Branches

  Several branches that are always open and that you use for different stages of your development cycle; you can merge regularly from some of them into others. For example: `master`, `develop` or `next`, `proposed` etc. The idea is that your branches are at various levels of stability; when they reach a more stable level, they’re merged into the branch above them.    

### Topic Branches  

  !!!! A topic branch is a short-lived branch that you create and use for a single particular feature or related work. E.g. JIRA issue-based branches (e.g. `AP-123`), `hotfix`. You may even go beyond this by having **small branches out of another small branches (e.g. experimenting along on half of another branch or so?)**. This technique allows you to context-switch quickly and completely, it’s easier to see what has happened during code review and such. You can keep the changes there for minutes, days, or months, and merge them in when they’re ready, regardless of the order in which they were created or worked on. **(This seems to be a good technique for testing on a few key concepts at once when decision should be made by another part, e.g. user, another team, etc.)**  
  
  It’s **important to remember** when you’re doing all this that these branches are completely local.  
  When you’re branching and merging, everything is being done only in your Git repository — there is no communication with the server.
  
### Remote Branches  

  Remote references are references (pointers) in your remote repositories, including branches, tags, and so on.  
  
  `git ls-remote [remote]` or `git remote show [remote]` - a full list of remote references, remote branch as well as more information on it.  
  
  !!! Remote-tracking branches are references to the state of remote branches. **They’re local references that you can’t move**; Git moves them for you whenever you do any network communication, to make sure they accurately represent the state of the remote repository. Think of them as bookmarks, to remind you where the branches in your remote repositories were the last time you connected to them.  
  
  Remote-tracking branch names take the form `<remote>/<branch>`.  
  
  !! `origin` is not special. `origin` is the default name for a remote when you run `git clone`. If you run  
  `git clone -o booyah` instead, then you will have `booyah/master` as your default remote branch.  
  
  `git fetch <remote>` - to synchronize your work with a given remote. This command looks up which server `origin` is (e.g, it’s git.ourcompany.com), fetches any data from it that you don’t yet have, and updates your local database, moving your `origin/master` pointer to its new, more up-to-date position.  
  
  `git remote add <name> <url>` - adds the a new remote reference to the project you’re currently working on.  
  
### Pushing
  
  `git push <remote> <branch>` - when you want to share a branch with the world, you need to push it up to a remote to which you have write access. Your local branches aren’t automatically synchronized to the remotes you write to — you have to explicitly push the branches you want to share.  
  
  !!! For example, `git push origin serverfix` - This is a bit of a shortcut. Git automatically expands the `serverfix` branchname out to `refs/heads/serverfix:refs/heads/serverfix`, which means, "Take my serverfix local branch and push it to update the remote’s serverfix branch."  
  
  `git push origin serverfix:awesomebranch` - push your local `serverfix` branch to the `awesomebranch` branch on the remote project.  
  
  `git config --global credential.helper cache` - set up a "credential cache", keep it in memory for a few minutes.  
  
  **It’s important to note** that when you do a fetch (`git fetch origin`) that brings down new remote-tracking branches, you don’t automatically have local, editable copies of them. In other words, in this case, you don’t have a new `serverfix` branch — you have only an `origin/serverfix` pointer that you can’t modify.  
  
  `git merge origin/serverfix` - to merge `origin/serverfix` branch into current working branch.
  
  `git checkout -b serverfix origin/serverfix` - create the local `serverfix` branch from the remote `origin/serverfix` one. Branch `serverfix` set up to track remote branch `serverfix` from `origin`. Switched to a new branch `serverfix`.  
    
### Tracking Branches
  
  Checking out a local branch from a remote-tracking branch automatically creates what is called a "tracking branch" (and the branch it tracks is called an "upstream branch"). Tracking branches are local branches that have a direct relationship to a remote branch. If you’re on a tracking branch and type `git pull`, Git automatically knows which server to fetch from and which branch to merge in.  
  
  When you clone a repository, it generally automatically creates a `master` branch that tracks `origin/master`.  
  
  `git checkout -b <branch> <remote>/<branch>`  
  is the same as `git checkout --track <remote>/<branch>`  
  is the same as `git checkout <branch>` (work only if the branch name you’re trying to checkout (a) doesn’t exist and (b) exactly matches a name on only one remote).  
  It means branch `<branch>` set up to track remote branch `<branch>` from `<remote>`. Switched to a new branch `<branch>`.  
  
  `git branch -u <remote>/<branch>` - if you already have a local branch and want to set it to a remote branch, or want to change the upstream branch you’re tracking, you can use the `-u` or `--set-upstream-to` option to `git branch` to explicitly set it at any time.  
  
  !!!! When you have a tracking branch set up, you can reference its upstream branch with the `@{upstream}` or `@{u}` shorthand. For example, If you’re on the `master` branch and it’s tracking `origin/master`, you can say something like `git merge @{u}` instead of `git merge origin/master` if you wish. 
  
  !!! `git branch -vv` - to see what tracking branches you have set up. This will list out your local branches with more information including what each branch is tracking and if your local branch is ahead, behind or both. It’s important to note that these numbers are only since the last time you fetched from each server. This command does not reach out to the servers, it’s telling you about what it has cached from these servers locally. If you want totally up to date ahead and behind numbers, you’ll need to fetch from all your remotes right before running this. You could do that like this `git fetch --all; git branch -vv`  
  
### Pulling
  
  `git pull` - will look up what server and branch your current branch is tracking, `fetch` from that server and then try to `merge` in that remote branch. Generally it’s better to simply use the `fetch` and `merge` commands explicitly as the magic of `git pull` can often be confusing.  
  
### Deleting Remote Branches
  
  !!!! `git push <remote> --delete <branch>` - remove the pointer from the server. **The Git server will generally keep the data there for a while until a garbage collection runs, so if it was accidentally deleted, it’s often easy to recover** (how???).  
  
  
## Rebasing
  
  `merge` and `rebase` - two main ways to integrate changes from one branch into another in Git.  
  With the `rebase` command, you can take all the changes that were committed on one branch and replay them on a different branch.  
  
### The Basic Rebase  
  
  `git checkout <branch1>`  
  `git rebase <branch2>`  
  This operation works by:
   - going to the common ancestor of the two branches (the one you’re on and the one you’re rebasing onto),  
   - getting the diff introduced by each commit of the branch you’re on,
   - saving those diffs to temporary files, 
   - resetting the current branch to the same commit as the branch you are rebasing onto, and finally 
   - applying each change in turn.  
   
  There is no difference in the end product of the integration, but **rebasing makes for a cleaner history**.  
  If you examine the log of a rebased branch, it looks like a linear history: it appears that all the work happened in series, even when it originally happened in parallel.  
  That way, the maintainer (let's say you are not one) doesn’t have to do any integration work — just a fast-forward or a clean apply.  
  
  !!!!! Note that the snapshot pointed to by the final commit you end up with, whether it’s the last of the rebased commits for a rebase or the final merge commit after a merge, **is the same snapshot — it’s only the history that is different**.  
  **Rebasing replays changes from one line of work onto another in the order they were introduced, whereas merging takes the endpoints and merges them together**.
  
### More Interesting Rebases  

  !!!! `git rebase --onto master server client` - Take the `client` branch, figure out the patches since it diverged from the `server` branch, and replay these patches in the `client` branch as if it was based directly off the `master` branch instead.  
  
  !!!! `it rebase <basebranch> <topicbranch>` - checks out the `topicbranch` for you and replays it onto the `basebranch` (e.g. master).  
  
### The Perils of Rebasing  
  
  !!!!! **Do not rebase commits that exist outside your repository and people may have based work on them.**  
  
  !!!!! **When you rebase stuff, you’re abandoning existing commits and creating new ones that are similar but different**.  
  If you push commits somewhere and others pull them down and base work on them, and then you rewrite those commits with `git rebase` and push them up again, your collaborators will have to re-merge their work and things will get messy when you try to pull their work back into yours.  
  
  `git push --force` - Usually, the command refuses to update a remote ref that is not an ancestor of the local ref used to overwrite it. `--force` flag disables the check, and can cause the remote repository to lose commits; use it with care.  
  
### Rebase When You Rebase  
  
  !!!!! It turns out that in addition to the commit SHA-1 checksum, **Git also calculates a checksum that is based just on the patch introduced with the commit. This is called a “patch-id”**.  
  If you pull down work that was rewritten and rebase it on top of the new commits from your partner, Git can often successfully figure out what is uniquely yours and apply them back on top of the new branch.  
  
  `git config --global pull.rebase true` - If you are using `git pull` and want to make `--rebase` the default, you can set the `pull.rebase` config value.  
  
  !!!!! If you only ever rebase commits that have never left your own computer, you’ll be just fine.  
  If you rebase commits that have been pushed, but that no one else has based commits from, you’ll also be fine.   
  **If you rebase commits that have already been pushed publicly, and people may have based work on those commits, then you may be not ok.**  
  If you or a partner does find it necessary at some point, make sure everyone knows to run `git pull --rebase` to try to make the pain after it happens a little bit simpler.  
  
### Rebase vs. Merge
  
  Merging is more like:  One point of view on this is that your repository’s commit history is a **record of what actually happened**. It’s a historical document, valuable in its own right, and shouldn’t be tampered with.  
  Rebasing is more like: The opposing point of view is that the commit history is the story of how your project was made. You wouldn’t publish the first draft of a book, and the manual for how to maintain your software deserves careful editing.
    
  !!!!! In general **the way to get the best of both worlds is to rebase local changes you’ve made but haven’t shared yet before you push them in order to clean up your story, but never rebase anything you’ve pushed somewhere**.  
  
  
## Git on the Server
  
  A remote repository is generally a bare repository — a Git repository that has no working directory. Because the repository is only used as a collaboration point, there is no reason to have a snapshot checked out on disk; it’s just the Git data. In the simplest terms, a bare repository is the contents of your project’s .git directory and nothing else.  
  
### The Protocols
  
  Git can use four distinct protocols to transfer data:  
  1. Local, 
  2. HTTP, 
  3. Secure Shell (SSH) and 
  4. Git.
    
#### Local Protocol
  
  The remote repository is in another directory on the same host.  
  This is often used if everyone on your team has access to a shared filesystem such as an NFS mount, or in the less likely case that everyone logs in to the same computer.  
  For example: `git clone /srv/git/project.git` (with the path - Git tries to use hardlinks or directly copy the files it needs)  
  Or: `git clone file:///srv/git/project.git` (with `file://` - Git fires up the processes that it normally uses to transfer data over a network, which is generally much less efficient.)  
  
  To add a local repository to an existing Git project, you can run something like this:  
  `git remote add local_proj /srv/git/project.git`  
  
  
  
  
  
  
  
  
  
  
    
  
  
  
  
  
  
  
  
  
    
  
  
  
  
  
  
  
  
  
  


...


 
    



