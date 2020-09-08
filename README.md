# Introduction

Working with git github and open source is not so easy for begineers. I have spent a lot of time to read tutorials and git commands but didnot learn enough.

Now, I am confident I need more practice like to create my own solutions, automated scripts and learn more by doing a lot of projects by recreating the device to practice more and more.

# How git fetch works

To understand how git fetch works we have to talk about how git organizes and stores commits. Behind scenes, in the ropository's `./.git/objects/` directory. All commits from local or remote branches are kept safely there,seperated through use of branch refs. Local branches inside ./.git/refs/heads and remote branches inside `./.git/refs/`remotes. We can see that if we type `$ git branch` or `$ git branch -r`. The same output as we type `ls ./.git/refs/heads/`

## Git fetch commands and options

```git
git fetch upstream
git fetch <remote>
git fetch <remote> <branch>
git fetch --dry-run
```

--dry-run option to perform a demo run ,fetch will not apply but example of output can be seen.

# Resetting, Checking Out and Reverting

These commands combines to affect out working directory, cached snapshots and commit history.

## Resetting

On our working directory if we have changed files and committed few times and if you just want to go back just because something is wrong, so git reset is the way to restore the state to a given commit and erase all newer commits permanently.

```git
 $ git reset --hard
 $ git reset --hard 766f
```

## Checking Out

This takes us back in commit history,while newer changes are preserved.Like Sci-fiction movie, if you edit and commit, you will be in new reality, a new branch.

```
$ git checkout 82f5
$ git checkout master
```

we can choose only to restore particular files and subdirectories by appending them after the command
$ git checkout 82f5 some.file another.file
$ git checkout :/"My first b"
\$ git checkout master~5

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

- Pull Request (Fork > Clone > Edit > PR)
- Sync and Develop (Fork > Clone > remote add UPSTREAM > fetch/Rebase > Push to origin)
- Branching git checkout -b new-branch creates and move to new branch. git branch -D branch to delete.
- Merge conflicts (Editing the file and git add file and commit)
- `$ git reset --hard to undo changes to last commit`
- `$ git reset --hard HEAD~2` This command Moves the current branch backward by 2 commits,while
- `git revert 389004d` is used to reverse a commit to a sha or undo a commit that has already been pushed to Github.
  [Undo a commit](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/undoing-a-commit.md)
- Stashing works with working directory which is saving its state while commit is saving
  changed state of the project.
- Saving a file in wordprocessing is similar to git Commit. Overwrite single file is saving
  a file in word processing while commit in git is about saving different states of a project
  by tracking multiple files and folders.
- SVN is central tracking with remote has original copy while git is distributed control
  system with copies with local and remote.

### References:

[Reference to first-contributions](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/additional-material.md)  
[why-should-i-use-git-instead-of-svn](https://stackoverflow.com/questions/740053/why-should-i-use-git-instead-of-svn) \
[git magic](http://www-cs-students.stanford.edu/~blynn/gitmagic/book.html) \
[git ready](http://gitready.com/) \
[Merging and rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
