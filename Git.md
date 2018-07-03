# Git

- What is the difference between "fast-forward-merge" and "non-fast-forward-merge"?  
It depends (the outcome is not `git-flow` dependent). `git log` won't give you the specific branch name (e.g. `feature/my-fancy-feature`). It will only give you the commit history with the message. Recalling the differences between fast-forward merging and non-fast-forward merging:  
fast-forward-merge (all commit history made in `feature/my-fancy-feature` will remain):  
`git merge`  
non-fast-forward-merge (all commit history made in `feature/my-fancy-feature` will be gone):  
`git merge --no-ff`  

- What is the difference between `revert` and `reset`?
<a href="#" title="...">⌘</a>

- **Explain: `git rm -r --cached . && git add . && git commit -am "Remove ignored files"`** 
Remove all of the items from the Git Index (not from the working directory or local repo), and then update the Git Index, while respecting git ignores. PS. Index = Cache  
Read more:  
https://stackoverflow.com/questions/1274057/how-to-make-git-forget-about-a-file-that-was-tracked-but-is-now-in-gitignore  
