# Merge conflicts
When we want to move changes from one branch to another, we use the git mergecommand. Depending on the history of our commits, we can merge two different ways:

1. Fast forward:  In fast forward merge, which is when git can easily tell when the commits happened and "put" one set of commits on top of another chronologically.
2. Recursive: When different commits happen at different times on two branches, and git can not easily determine what order these commits happened in, a recursive merge needs to happen. 
```
mkdir merge_conflicts
cd merge_conflicts
git init
echo first > first.txt
git add .
git commit -m "first commit"

git checkout -b new_branch
echo second > second.txt
git add .
git commit -m "adding second.txt"

git checkout master
echo something_else > second.txt
git add .
git commit -m "adding second.txt on the master branch"
```
This final command should output

```
Auto-merging second.txt
CONFLICT (add/add): Merge conflict in second.txt
Recorded preimage for 'second.txt'
Automatic merge failed; fix conflicts and then commit the result.
```

Looks like we have an issue because when we tried to merge the new_branch, git does not know which second.txt file to use! Both branches have a file with the same name, but different contents.

git merge new_branch
```
```
something_else  
\=======  
second  
\>>>>>>> new_branch
```
Delete the line so that second.txt file looks like:
```
second
```

This is our way of letting Git know that we want to keep the text from new_branch and discard the text from master.

Then let's go back to the terminal and run
```
git add .  
git commit -m "fixing merge conflict"
```
Conclusion: To resolve conflicts, Git will put the two conflicting pieces of text right on top of one another; the only thing you need to do is decide what text you want to keep, delete the character separating the two options (======= and >>>>>>>), and add and commit the results of your manual merge.