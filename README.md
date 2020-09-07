# Pull Request
 Fork > Clone > New branch > Make Changes > Push branch to Origin > Compare & Pull Req.

> Fork from Public repo
> git clone url
> git checkout -b new_branch-name
> Make changes - May be start with documentation to your open source repo
> git push origin branch 
> Going to github repository, on right click compare and Pull request
> Compare Local branch and Public repo master branch 
> new Pull Request. If maintainer of Public repo likes the changes He/She merges.

# Sync your local working copy of repo with Public Repo
 Once you fork and clone a project repo, You normally want to work on it in local machine.
> .git folder is already created to track changes.
> Master branch is created and HEAD pointing it.
> local repo has remote branch origin and local has url to push master branch to github 
Over Time Public repo you forked your copy of working directory changes. To copy changes, an upstream is created and pulled into local working directory. And Pushed to Origin.
> git remote add upstream url-Public
> git pull upstream master

or 
> git fetch upstream
> git rebase upstream/master
> git push origin master

# Common Workflows
 
* Pull Request (Fork > Clone > Edit > PR)  
* Sync and Develop (Fork > Clone > remote add UPSTREAM > fetch/Rebase > Push to origin)
* Branching git checkout -b new-branch
* Merge conflicts (Editing the file and git add file and commit)
* Stashing works with working directory which is saving its state while commit is saving 
changed state of the project. 
* Saving a file in wordprocessing is similar to git commit. overwrite single file vs 
 tracking multiple files and folders.
* SVN is central tracking with remote has original copy while git is distributed control system. 
