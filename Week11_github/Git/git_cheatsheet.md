## Git cheatsheet

Version Control Systems (VCS) allow you to track software revisions over time and help a team manage changes over time.

One of the most popular VCS is [git](https://git-scm.com/). Git records the history of changes as a stream of snapshots. 
Git is a distributed VCS (every team member's copy of the code will contain the
full history of changes) rather than having one single place for recording the 
history of changes. 

Git is not the same as [GitHub](https://github.com/), Git is a VCS for managing your
code history, GitHub is a hosting service for your Git repos. 
There are other hosting services besides GitHub, 
Butbucket is another popular one. 
You can create a new repo from [GitHub](https://www.github.com) and sign-up or login if
you've already gotten an account.
In the right hand corner pick the "New Repository" under the "+" sign, name it, and follow the
instructions.

### Initializing a git repo:
First you need to have git installed from [here](https://git-scm.com/downloads).

If you dont have a folder for your code make one or navigate to one:
```
mkdir my_git_repo
cd my_git_repo
```

To turn that folder into an empty git repo:
```
git init
```
To see the files generated type:
```
ls -a 
```
To track files you first need to see the status of your file:

```
git status
```

A file can be (1) not tracked; (2) staged; and (3) commited
Create a file in your repo folder:

```
touch readme.txt
git status readme.txt
```

To ensure the file readme.txt is tracked we need to "stage" it by using:

```
git add readme.txt
git status
```

If you don't want git to track certain files (e.g., data files are typically large and you don't want to track them or they may contain sensitive info such as an API key) you need to tell git to "ignore" them (add as many files to .gitignore as you want, 
but ensure you add comments `##` to remember why you've ignored them):

```
touch passwords.txt
touch .gitignore
```
Add some info to the passwords.txt and to the .gitignore file:

```
echo "123456" >> password.txt
echo "passwords.txt" >> .gitignore
git status
```
Git status will show that files are staged but not commited,
to unstage:
```
git rm --cached <file>
```
To commit use the git commit command, which saves the state of your project by adding snapshots of staged files to the repository. The command
can include the "-m" flag w/ a message describing what we've changed:

```
git commit -m "modified the function that downloads data"
```

Doing a git status now after git commit verifies that tracked files are up to date. ONLY changes to staged files (using git add) will be added to the repository with the git commit command.
To commit modifications for every tracked file in the repo use:

```
git commit -a -m "commit all"
```

However, this approach does not allow specific comments for each file.

To see the history of all commits use:
```
git log
```

The command lists all commits in inverse order, dates, authors, and some other related information about each commit.

Sometimes we may have committed some files that should not have been pushed to your Git repository, and we may want to perform additional changes before issuing the commit, so we need to undo the last commit.

To undo the commit, just run the command:

```
git reset --soft HEAD~1. 
```
The last commit will be removed from your Git history. If you are not familiar with this notation, “HEAD~1” means that you want to reset the HEAD (the last commit) to one commit before in the log history.

``` 
git log --oneline

3fad532  Last commit   (HEAD)
3bnaj03  Commit before HEAD   (HEAD~1)
vcn3ed5  Two commits before HEAD   (HEAD~2)

```

After commiting the changes, the next step is pushing the local repo to the git server on a remote location such as GitHub/Bitbucket.

After creating the remote repository we have 2 options:

1: download/clone the repo and start making changes  
2: initialize a local repo and connect it with the remote one

1) The clone command is used to download a remote repo (cloning should be done at the very start of the project!):

```
git clone https://www.github.com/user/project_name.git  
```

2) If you have already initialized a local repo you can
connect it to the remote one using the following command:

``` 
git remote add origin:https://www.github.com/user/project_name.git
```

### Pushing

Pushing remotely - after making our local changes and commits
it's time to push the changes to the remote repo. The push command tells git where to put our commits (remote is origin and the default local branch name is master/main):

```
git push -u origin master  
```

"-u" tells Git to remember the parameters so the next time
we can simply run the command below, and Git will know what to do.

```
git push
```

Keep in mind that pushing to a remote location (GitHub/Bitbucket) is not a must but highly recommended.

### Pulling

Pulling: A local repository may have commits pushed by other
users who work on the repo. Get the latest updates, esp when you are not the only one working on the project.
We can check for changes on our GitHub repo and pull down any new changes:

```
git pull origin master
```

We can check what is different from our last commit by using the git diff (we want the diff our most recent commit, which we can refer to):

```
git diff HEAD
```

Using the HEAD pointer.

Reset and Checkout we can use diff to look at changes within files that have already been staged. Running the code below will show the changes you just staged.

```
git diff --staged
```

A stage can also be reset by using the reset command:
```
git reset 'filename'
```

This command removes the file from the stage status, meaning
all the changes will still remain in the file.

To reset the file to the latest committed version, the checkout command can be used:

```
git checkout -- "file name"
```

It's good practice to regularly run git diff and reset files you accidently changed.

### Branching

Branches: branches are a very imp part of git allowing you to 
make a copy of the working project and change it without affecting 
the main branch (master branch), giving an opportunity to work on the 
same project with different commits.  
When you want to add a new feature or fix a bug - no matter how big or
how small - you create a new branch to encapsulate your changes.

After the feature is done, you can merge it with the master branch.
Creating a new branch is done with the branch command:

```
git branch my_new_branch
```

Then we need to switch to the branch using the checkout command:

```
git checkout my_new_branch
```

There is a shortcut to do both in one command:

```
git checkout -b my_new_branch
```

This shows all branches including the new one, my_new_branch

```
git branch -a
```

Now every change made in my_new_branch will affect the master branch.  

This means you can safely work on the project w/out breaking anything.
Each branch has its own history, staging area, and working directory.

In order to see the list of your branches in the project directory, run the command:

```
git branch
``` 

Ammend: this is a convenient way to modify the most recent commit. It lets you combine staged changes w/ the prev commit instead of creating an entirely new commit. It can also be used to modify the prev commit message:
```
git commit --amend
```
```
git commit --amend -m "updated commit message"
```

"-m" allows you to pass in a new message for the latest commit. 
Amending doesn't only alter the most recent commit, it replaces it
entirely, meaning the amend commit will be a new entity.

Stash: it temporarily caches any changes you've made to your working copy so you can switch to sth else, and then come back and recover them later.

```
git stash
```

The git stash command takes your uncommited changes, both staged and
unstaged, and saves them for later use.

After stashing you're free to make any changes, create new commits,
switch branches, and perform any other git operations. Then
you can come back and re-apply your stash.

The stash stays on your Git repo. They will not be transfered 
to the server when you push. 

There are 2 ways to re-load/re-apply the stashed changes.
Pop will remove stashed changes from the stashed state:

```
git stash pop
```
Apply applies the same stashed changes to multiple branches:
```
git stash apply
```

Git stash will not include untracked files by default. To
do so you need to add -u option/ --include-untracked.

### Merging Branches 

Let's create and commit a few files on the master branch
aka main branch:

```bash
touch file{1..5}.txt
git add .
git commit -m "add files 1 to 5"
git checkout -b test 
```

At this point this is identical to main branch
but every modification, addition, removal is done in the context of this
"new" test branch. Let's add new files and remove a couple of the 
already existing files and then commit the changes:

```
touch file{6..10}.txt
git rm file3.txt
git rm file4.txt
git add .
git commit -m "add new files, remove 3&4"
```

While we could use just rm instead of git rm it's better to use
git rm which will not only rm the files from the disk but will also
stage the removal of files for us.

Now we have 2 branches master and test. We are on the test branch 
which contais some new files and lacks some of the files from the 
main branch bc we removed them. Let's switch to the main 
branch and finally merge them together. Git merge test tells git to merge the test branch into the 
current branch (the main branch in our example).

```
git checkout main
git merge test
```


In order to remove a branch that you don't need anymore, use:

```
git branch -d test 
```
### Merging conflicts 

Let's see what happens if we change the same
file in two different branches and then try to merge the branches 
together. 

Create file1.txt with the following text and commit the change:

"This is the original text. We want to explain how merge conflicts
happen. Follow the instructions and steps correctly."

Now let's create a new branch "test" and edit file1 by adding the following
text after the initial one:  

"But we also want to add some text here in the branch 'test'."
Again commit your changes and switch back to the master branch.

```
git checkout -b test
nano file1.txt
git add file1.txt
git commit -m "add new text in test branch"
```
This time add the text below in file1 and commit your changes:
"But we also want to add text here in main's branch file1.txt"

```
git checkout main
nano file1.txt
git add file1.txt
git commit -m "add text in branch main"
```

Now we have file1 with 2 different variants in 2 different branchs (main and test). Let's merge them and see what will happen:

```
git merge test
```

The result of the merge is: merge conflict in file1 
Because there were 2 different versions of the file, Git failed
to merge them together automatically. We should fix this
conflict manually and commit the change.

First, let's do a git status. It shows which file resulted in the merge
conflict, useful when having multiple files. It also suggest how to fix
the conflict and commit or abort the merge. 
When a merge conflict occurs, Git automatically adds some indicators to
make it easy for us to find where the conflict occurs. These indicators are:

```
<<<<<<<, =======, and >>>>>>>
Use the content before ======= is the receiving branch and the part after this
marker is the merging branch. 
<<<<<<< HEAD
This is the original text. We want to explain how merge conflicts
happen. Follow the instructions and steps correctly. But we also 
want to add text here in master's branch file1.txt
=======
This is the original text. We want to explain how merge conflicts
happen. Follow the instructions and steps correctly. But we also 
want to add some text here in the branch 'test'.
>>>>>>> test
```
Now, it's your choice to keep only your main branch changes, or
make a brand new change, which may incorporate changes from both.
After that, delete the conflict markers and make the changes you want.
Save and exit and commit your changes. 

If in your branch you deleted a file/s it will merge seamlesly and delete
the files even in master, so you need to ensure you dont do that
the merge conflicts only occur if you edited the exact same text location.


