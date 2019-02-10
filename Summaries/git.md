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
- ...
