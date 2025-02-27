# Introduction

### Create a new Repository
`git init` will create a git repository on local machine on a new project.
`git clone` will download remote repo on local machine. It creates a default link to remote repo called origin.Create a working copy of a local repo without server and Using a remote Server
`git clone /path/toRepo` 
`git clone username@host:/path/toRepo`. After a While if we want to download the updates we need to pull code
`$git pull` or `git pull --rebase` if pull and if fetch `git fetch upstream` and `git merge REMOTE_BRANCH`.

# What is Commit? 
Likewise committed to a relationship, or being committed to a set task completion its similar meaning in world of History making in Git.
Some Basic Commands are 
- git add .   ----- add files desired dot can be replaced with filename or filenames.
- git status  ----- state of the files
- git commit -m "Message to save" --- saving changes to source control
- git log ----- Showing the saved messages and overall project state.   

There are other variations of these basic commands using flages like -- no log --online -a etc.

Git commit is nothing but a state of our files. Like saving a file after typing a document. What if we update after saving, we lose the state we saved our files last time. If we did a commit, we could go back after saving second time update. 
`$ git checkout k32k`  
- When we make a commit, it is stored with a name that provides reference to that commit, k32k in our example is that name called _sha_.
- We can commit using `$ git commit -a -m 'Commit message' ` or `$git commit -a` which skips a step of staging. Well staging is a temporary step, to decide, go back or forward. 
- We can always go back the git tree using previous `checkout` command and
 `$ git reset --hard` if files are not commited
 `$ git reset --hard 2de2` if files are commited but this step deletes all later commits,
 - `$ git checkout k32k` as seen before is safer that lets return to recent commit using `$ git checkout master`.
 - Set up upstream if git push fails with fatal error. `fatal: The current branch gh-pages has no upstream branch.`
 `git push --set-upstream origin gh-pages`  
 
# Resetting, Checking Out and Reverting

These commands combines to affect out working directory, cached snapshots and commit history.

## Checking Out

This takes us back in commit history,while newer changes are preserved.Like Sci-fiction movie, if you edit and commit, you will be in new reality, a new branch.

```
$ git checkout 82f5
$ git checkout master~  ### LAST COMMIT
```
## Resetting

On our working directory if we have changed files and committed few times and if you just want to go back just because something is wrong, so git reset is the way to restore the state to a given commit and erase all newer commits permanently.

If we are just starting and make changes to few files, but didnot commit and want to discard changes then `reset --hard` can reset to the last commit.
 ```$ git reset --hard```
 Permanently wipe the newer changes, and go back steps to a stable state
 ```$ git reset --hard 766f```

#### Recovering deleted files not commited
Yesterday I started to use git repository on cPrograms folder with some files. I did `$ git init` and afterwards thought I need to organize my files into folders so
I wanted to get rid of git init. Obvious, options are to delete a .git repository but I thought of git reset command would do it and tried
`git reset --hard`. To my surprise, I lost all files when I tried to open that folder in vscode.Upon search online, I found this [Recovering deleted files not commited](https://stackoverflow.com/questions/12434618/can-deleted-files-that-are-added-but-not-committed-in-git-be-recovered) link and commands
`git fsck --lost-found` and `git cat-file -p SHA1` found git writes all dangling objects into the .git/lost-found/commit/ or .git/lost-found/other/ folders. So relieved!! that I 
can recover all files using sha1 of filenames of blob that I had to recoved all files manually.


### Remove files from staging 
`$ git rm --cached * ` remove all files added by `$ git add .`
`$ git rm --cached name-of-file.md` for single file.

#### Files
We can choose only to restore particular files and subdirectories by appending them after the command
`$ git checkout 82f5 some.file another.file`
#### Select by Commit Meessage and a number of commits back using `master~number`
`$ git checkout :/"My first b"`
`$ git checkout master~5`

## Reverting

git revert will undo just the commit with the given hash. The revert is recorded as a new commit, which you can confirm by running git log.
`git revert sha2`

# Git log and git diff

```
$ git log

$ git diff 
$ git diff "@{yesterday}
$ git diff 1b6d "master~2"
$ git whatchanged --since="2 weeks ago"
```

# How git fetch works

To understand how git fetch works we have to talk about how git organizes and stores commits. Behind scenes, in the ropository's `./.git/objects/` directory. All commits from local or remote branches are kept safely there,seperated through use of branch refs. Local branches inside `./.git/refs/heads` directory and remote branches inside `./.git/refs/remotes` directory . We can see that if we type `$ git branch` or `$ git branch -r`. The same output as we type `ls ./.git/refs/heads` or `ls ./.git/refs/remotes`.
Git fetch is used to download files from remote repository from other person. We need a link to their remote repo. That link is added with 
- `$ git remote add origin remote_url_of_other_person` add a reference to remote repo to download or upload as origin
- `$ git fetch origin master`
- `$ git merge` 
- Conflicts can occur, we resolve that in our text editor by removing unwanted changes, and make another
 commit. We make another commit if we remove a commit using ` $ git revert` .
 
### Origin is a shortname for remote repository
Our remote repository on github has a name like awesome_Project, proj_xyz and if we want to connect to our remote repo we need a URL of our remote repo. So, instead of typing URL we give it a name, that is origin, we can give any other names.
- `$ git remote add origin URL_remote_awesome_Project`
- `$ git remote add origin URL_remote_OpenSource_Proj`
- - `$ git remote add upstream URL_remote_OpenSource_Proj`
Git stores seperate origin for each of different remote repository.

## Pull is alternative that combines fetch and merge.
- `$ git pull`

## Git fetch commands and options

```git
git fetch upstream
git fetch <remote>
git fetch <remote> <branch>
git fetch --dry-run 
```

--dry-run option to perform a demo run ,fetch will not apply but example of output can be seen.

# Pull Request

Fork > Clone > New branch > Make Changes > Push branch to Origin > Compare & Pull Req.

- Fork from Public repo
- `git clone url`
- `git checkout -b new_branch-name`
- Make changes - May be start with documentation to your open source repo
- `git push origin branch `
- Going to github repository, on right click compare and Pull request
- Compare Local branch and Public repo master branch
- New Pull Request.
  > If maintainer of Public repo likes the changes He/She merges.
  > ![Pull Request snapshot](/images/PullReq.png) > [How to make Pull Request i.e. make changes to merge with public repo](https://github.com/firstcontributions/first-contributions)

# Sync your local working copy of repo with Public Repo

Once you fork and clone a project repo, You normally want to work on it in local machine.
On this point in local project, we already have:

- .git folder is already created to track changes.
- Master branch is created and HEAD pointing it.
  > local repo has remote branch origin and local has url to push master branch to github
  > Over Time Public repo you forked your copy of working directory changes. To copy changes, an upstream is created and pulled into local working directory. And Pushed to Origin.
- `git remote add upstream url-public-repo`

  > Merge confilcts can happen when we pull or do a fetch. Which means editing the proposed
  > changes and desired changes. Next steps can be done in two ways using pull or fetch/rebase.

- ` git pull upstream master`

or another way to pull from original project is like: ![add upstream snapshot](/images/addUpstream.png)

```
$ git fetch upstream/origin/<any remote branch>  // So the branch is downloaded
$ git checkout master  // head to master or branch
or
$ git checkout -b feature_branch
Finally merge the <remote> to <master>
$ git merge origin/master

$ git rebase upstream/master
$ git push origin master
```

Alternative to fetch is rebase which rewrites the commit history. So with fetch we have fetch>checkout>merge cycle to be remembered.

[How to Sync your fork with Public repo](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/keeping-your-fork-synced-with-this-repository.md)

# Common Workflows

- Pull Request `(Fork > Clone > Checkout Branch + Edit > Push to Remote repo = PR)`
- Sync and Develop `(Fork > Clone > git remote add UPSTREAM > fetch/Rebase > Push to origin)`
- Branching commands `git checkout -b new-branch` creates and move to new branch. `git branch -D branch` to delete.
- Merge conflicts (Editing the file from similar duplicate code sections to select one section and 
  remove any git `<--Code changes on first section->>` like syntax before doing `git add fileName` and rebase or abort,
  `$ git rebase --continue or --abort`
- `$ git reset --hard to undo changes to last commit`
- `$ git reset --hard HEAD~2` This command Moves the current branch backward by 2 commits,while
- `git revert 389004d` is used to reverse a commit to a sha or undo a commit that has already been pushed to Github.
  [Undo a commit](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/undoing-a-commit.md)
- Stashing works with working directory which is saving its state while commit is saving
  changed state of the project. To apply stash `$ git stash apply` or to list stack of stash `$ git stash list`.
- Sometimes a project wouldnot be pushed to remote origin because of recent changes, if you want to push and not ready to commmit just do, `$ git stash`.
  and sometimes you cannot push to remote, it happens when we pull the changes in remote to any feature branch, so to avoid this always make sure you are 
  in master branch before a pull . so `$ git checkout master` followed by `$ git pull` or `$ git pull upstream master` 
- Saving a file in wordprocessing is similar to git Commit. Overwrite single file is saving
  a file in word processing while commit in git is about saving different states of a project
  by tracking multiple files and folders.
- SVN is central tracking with remote has original copy while git is distributed control
  system with copies with local and remote.       
- [Feature Branching Workflow](https://gist.github.com/blackfalcon/8428401) This gist on git workflow, provides
  easy to follow guide for a project which explains git branching, checking out to remote branches, git pull while staying current to master or root
  directory so that staying sync with github repo makes creating features on team projects fun. Rebasing is also explained well along with alias in bash_profile. 
- To rebase your local feature branch off of the latest version of master, following these steps will be a guarantee every time.

```$ git checkout master         /* ensure you are on the master branch
   $ git pull                                   /* pull the latest from the remote 
   $ git checkout my-feature-branch      /* checkout the feature branch
   $ git push origin my-feature-branch  /* update your copy in the repo
   $ git rebase master              /* rebase on the master branch
   $ git push origin my-feature-branch --force   /* force update the remote
```

### References:

[Reference to first-contributions](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/additional-material.md)  
[why-should-i-use-git-instead-of-svn](https://stackoverflow.com/questions/740053/why-should-i-use-git-instead-of-svn) \
[git magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/book.html) \
[git ready](http://gitready.com/) \
[Merging and rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing).  
[Think like a git](http://think-like-a-git.net/)  
[Merge-conflicts](./merge-conflicts.md)

[Different flags with important usage Git rebasea and EC2 AWS server connection](./i-flag.md)
