# Pro Git, Version 2.1.109, 2019-02-04, by Scott Chacon and Ben Straub

Reading: https://github.com/progit/progit2/releases/download/2.1.109/progit.pdf  
Latest version: https://git-scm.com/book/en

## Preface

- Both authors worked/work for Github company

## Getting Started

- Version control is a system (VCS) that records changes to a file or set of files over time so that you can recall specific versions later.  

### Local Version Control Systems
- No more manual copying directories or files, naming `...v1.ext`, `...v2.ext`, etc. with git.
- RCS was first released in 1982 by Walter F. Tichy at Purdue University. It was an alternative tool to the then-popular *Source Code Control System (SCCS)* which was nearly the first version control software tool (developed in 1972 by early Unix developers). RCS works by keeping patch sets (that is, the differences between files) in a special format on disk; it can then re-create what any file looked like at any point in time by adding up all the patches. With RCS, users can make their own revisions of a document, commit changes, and merge them. RCS was originally developed for programs but is also useful for text documents or configuration files that are frequently revised. RCS operates only on single files. It has no way of working with an entire project, so it does not support atomic commits affecting multiple files. Although it provides branching for individual files, the version syntax is cumbersome. Instead of using branches, many teams just use the built-in locking mechanism and work on a single *head branch*. Read more: https://en.wikipedia.org/wiki/Revision_Control_System

### Centralized Version Control Systems
- CVS, Subversion, Perforce, etc. - Centralized Version Control Systems (CVCSs). These have a single server that contains
all the versioned files, and a number of clients that check out files from that central place.
- ...
