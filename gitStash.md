# Stashing is to save changes to a file temporarily.

Some important tasks need before we commit 
changes on a branch. We issue Commands: 

- $ git stash 
- $ git stash list 
- $ git stash apply 
- $ git stash pop 

# Clean project by removing untracked 
Files and folders

- $ clean -n # files
- $ clean -d # directories
- $ clean -f 

- $ git restore .
- $ git checkout .
Git restore is newer command does exactly
Like git checkout. Clean tracked changes.
But leave untracked files and folders, 
So, git clean helps with that.

# Merge conflict happens when we merge branches 
To main branch, when someone else already merged
Changes to main before on same file.
# Resolves editing file with changes we want to 
Keep and deleting rest we don't need.
-  # git commit --amend 
To change last commit without making new commit.
