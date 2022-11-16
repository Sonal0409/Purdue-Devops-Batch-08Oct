Day 3:
*********************




Git reset command and its options

 Git reset command:

This command is applied on your commit history

This command is used when you want to discard changes done as part of multiple commits

This command will also delete your commit ids, you will not be able to see the ids

Reset command with its option --hard 
can remove changes and commit ids 
hence it is also called as a destrcutive command

Once reset command is executed it never generates a commit id or there is no log for its operation 

When we use the reset command, we are resetting the HEAD of the commits

git reset --hard <commitid>

Other rest options that are safe to use and used frequently are:

 git reset --soft <commitid>

The <commitid> becomes the head and orphan commit id will be deleted fromlog and 
files or changes will move back to staging area
 

 git reset --mixed <commitid>


The <commitid> becomes the head and orphan commit ids will be deleted from log and files or changes
 will move back to Unstaged area
 

hard->will delete permanently from WD,staging area,LR
soft->will delete permanently from LR and files will be available in WD and staging area
mixed->will delete permanently from LR and staging area and files will be available in WD


Branching , Merging and rebasing
*********************************************
Branching is a concept in git which allows to you freely work on multiple features at he same time without impacting the main master branch

Whenever we do  commits on our repository we have seen a branch named master which gets updated.

Master branch is the default branch which get created upon initializing a repo

You can create any number of branched, a branch is copy of  master branch

You can switch to a branch and work/develop on it.
Once development or changes are complete on a branch , you can merge it to master branch

You can also rename and delete a branch.

But you cannot delete the master branch.







Scenario 1:  Create branches in Local repo

> Command to check how many branches are  in Local repo

	…
	git branch
           …

> Create a new branch in our Local repository
	…
	 git branch f1
 	…

> Switch to a particular branch 
       …
       git checkout f1
      …

> Add new file and commit on the branch f1
	$ touch feature1
	$ git add .
	$ git commit -m “added onf1”

	$ git log –oneline  // check the new commit

> Switch back to master branch and compare the 2 branches

	…
 	git checkout master
 	…

Assignment
> Compare the 2 branches:
…

git diff --name-status master..f1

…
OR

git diff master..f1



Scenario 2:

> Command to create a new branch as well as switch to new branch
	…
	 git checkout -b f2
	…

> Add new file and commit on the new branch

> Switch back to master

Scenario 3: Merge the changes from feature branch to master

> Always switch to the branch where you want to merge the files from feature branch
	…
	git checkout master
	…

> Merge the changes from new branch to master branch
	…
	 git merge <sourcebranch> <destinationbranch>
	…
	
	…
	git merge f1 master
	…
> Check the commit history on master

Scenario 4:

Change the name of the branch
	…
	git branch -M f1 dev
	…

Delete a branch in local:

Make sure , you are not on the branch that is to be deleted

First checkout to master branch
	…
	 git checkout master
	…

…	
git branch -D f2
…

List of branches that have not been merged to master


git branch --no-merged

List of branches that have been merged to master

git branch --merged

Cherry-pick scenario:
******************************
...
 git branch
...
  git checkout f2
...
   ls
...
  touch login
...
 git add .
...
 git commit -m "f2 login"
...
   touch sonal
  ...
   git add .
  
  ...
  git commit -m "f2 sonal"
  ...
  
   git log --oneline
  ...
   git checkout master
  ...
  git cherry-pick 66922bf f86a4c9
  ...
  ls

