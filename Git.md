# Git

- What is the difference between "fast-forward-merge" and "non-fast-forward-merge"?  
It depends (the outcome is not `git-flow` dependent). `git log` won't give you the specific branch name (e.g. `feature/my-fancy-feature`). It will only give you the commit history with the message. Recalling the differences between fast-forward merging and non-fast-forward merging:  
fast-forward-merge (all commit history made in `feature/my-fancy-feature` will remain):  
`git merge`  
non-fast-forward-merge (all commit history made in `feature/my-fancy-feature` will be gone):  
`git merge --no-ff`  

- What is the difference between `revert` and `reset`?
<a href="#" title="...">⌘</a>
