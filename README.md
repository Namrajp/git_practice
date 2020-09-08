# Pull Request
 Fork > Clone > New branch > Make Changes > Push branch to Origin > Compare & Pull Req.

* Fork from Public repo
* `git clone url`
* `git checkout -b new_branch-name`
* Make changes - May be start with documentation to your open source repo
* `git push origin branch `
* Going to github repository, on right click compare and Pull request
* Compare Local branch and Public repo master branch 
* New Pull Request.
> If maintainer of Public repo likes the changes He/She merges.
[How to make Pull Request i.e. make changes to merge with public repo](https://github.com/firstcontributions/first-contributions)

# Sync your local working copy of repo with Public Repo
 Once you fork and clone a project repo, You normally want to work on it in local machine. 
On this point in local project, we already have:
* .git folder is already created to track changes.
* Master branch is created and HEAD pointing it.
> local repo has remote branch origin and local has url to push master branch to github 
Over Time Public repo you forked your copy of working directory changes. To copy changes, an upstream is created and pulled into local working directory. And Pushed to Origin.
* `git remote add upstream url-Public-repo`
> Merge confilcts can happen when we pull or do a fetch. Which means editing the proposed 
changes and desired changes. Next steps can be done in two ways using pull or fetch/rebase
` git pull upstream master`

or 
 ```$ git fetch upstream
 $ git rebase upstream/master
 $ git push origin master
 ```
[How to Sync your fork with Public repo](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/keeping-your-fork-synced-with-this-repository.md)
# Common Workflows
 
* Pull Request (Fork > Clone > Edit > PR)  
* Sync and Develop (Fork > Clone > remote add UPSTREAM > fetch/Rebase > Push to origin)
* Branching git checkout -b new-branch creates and move to new branch. git branch -D branch to delete.
* Merge conflicts (Editing the file and git add file and commit)
* `$ git reset --hard to undo changes to last commit`
* `$ git reset --hard HEAD~2` This command Moves the current branch backward by 2 commits,while 
* `git revert 389004d` is used to reverse a commit to a sha or undo a commit that has already been pushed to Github.
[Undo a commit](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/undoing-a-commit.md)
* Stashing works with working directory which is saving its state while commit is saving 
changed state of the project. 
* Saving a file in wordprocessing is similar to git Commit. Overwrite single file is saving
 a file in word processing while commit in git is about saving different states of a project
 by tracking multiple files and folders.
* SVN is central tracking with remote has original copy while git is distributed control
 system with copies with local and remote. 

[Reference to first-contributions](https://github.com/firstcontributions/first-contributions/blob/master/additional-material/git_workflow_scenarios/additional-material.md)
