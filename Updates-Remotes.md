- Github has renamed its master branch main.

## Remote is git repo on github. 
It can be named anything but most common is origin and upstream. 
So, origin is name of github repo of our local git project.
Also, this repo have branches by default like master and recent name main.
### To create: 
`git remote add origin https://github.com/Namrajp/Your-name.git`

### To Remove:
`git remote remove origin`.

### To Push into newly created remote:
`git push --set-upstream origin master`

### To see remote url and info

```git config --get remote.origin.url```
or
```git remote show origin```

### To Pull from remote
```git pull origin main```
or
```git fetch origin main```

### To merge downloaded remote repo using pull or fetch

```git merge origin/master```
or
``` git rebase upstream master```

__Note__: To merge to a branch on local, we need to ***navigate to that branch*** first using 
```git checkout branch-name```
or to new branch using
``` git checkout -b branchName```

