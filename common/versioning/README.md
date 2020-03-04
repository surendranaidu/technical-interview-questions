# Code Versioning Interview questions

References:
1. https://www.edureka.co/blog/interview-questions/git-interview-questions/
2. https://career.guru99.com/top-40-interview-questions-on-git/

* **What is the difference between GIT and SVN?**

The difference between GIT and SVN is:

a)  	Git is less preferred for handling extremely large files or frequently changing binary files while SVN can handle multiple projects stored in the same repository.

b)  	GIT does not support ‘commits’ across multiple branches or tags.  Subversion allows the creation of folders at any location in the repository layout.

c)   	 Gits are unchangeable, while Subversion allows committers to treat a tag as a branch and to create multiple revisions under a tag root.

* **What is GIT stash?**

GIT stash takes the current state of the working directory and index and puts in on the stack for later and gives you back a clean working directory.  So in case if you are in the middle of something and need to jump over to the other job, and at the same time you don’t want to lose your current edits then you can use GIT stash.

* **What is GIT stash drop?**

When you are done with the stashed item or want to remove it from the list, run the git ‘stash drop’ command.  It will remove the last added stash item by default, and it can also remove a specific item if you include as an argument.

* **How will you know in GIT if a branch has been already merged into master?**

**git branch --merged** lists the branches that have been merged into the current branch
**git branch —-no-merged** lists the branches that have not been merged

* **What is ‘head’ in git and how many heads can be created in a repository?**

A ‘head’ is simply a reference to a commit object. In every repository, there is a default head referred as “Master”.  A repository can contain any number of heads.

* **What is the common branching pattern in GIT?**

The common way of creating branch in GIT is to maintain one as “Main“ branch and create another branch to implement new features. This pattern is particularly useful when there are multiple developers working on a single project.

* **What is a ‘conflict’ in git?**

A ‘conflict’ arises when the commit that has to be merged has some change in one place, and the current commit also has a change at the same place. Git will not be able to predict which change should take precedence.

* **How can conflict in git resolved?**

To resolve the conflict in git, edit the files to fix the conflicting changes and then add the resolved files by running “git add” after that to commit the repaired merge,  run “git commit”.  Git remembers that you are in the middle of a merger, so it sets the parents of the commit correctly.

* **What is another option for merging in git?**

“Rebasing” is an alternative to merging in git.

* **What is the syntax for “Rebasing” in Git?**

The syntax used for rebase is “git rebase [new-commit] “

* **What is the function of ‘git checkout’ in git?**

A ‘git checkout’ command is used to update directories or specific files in your working tree with those from another branch without merging it in the whole branch.

* **What is git stash?**

Often, when you’ve been working on part of your project, things are in a messy state and you want to switch branches for some time to work on something else. The problem is, you don’t want to do a commit of half-done work just so you can get back to this point later. The answer to this issue is Git stash.

Stashing takes your working directory that is, your modified tracked files and staged changes and saves it on a stack of unfinished changes that you can reapply at any time.


* **What is the function of ‘git stash apply’?**

When you want to continue working where you have left your work, ‘git stash apply’ command is used to bring back the saved changes onto the working directory.

* **What is git stash drop?**

Git ‘stash drop’ command is used to remove the stashed item. It will remove the last added stash item by default, and it can also remove a specific item if you include it as an argument. Now give an example.

If you want to remove a particular stash item from the list of stashed items you can use the below commands:

    git stash list: 

It will display the list of stashed items like:

    stash@{0}: WIP on master: 049d078 added the index file
    stash@{1}: WIP on master: c264051 Revert “added file_size”
    stash@{2}: WIP on master: 21d80a5 added number to log
If you want to remove an item named stash@{0} use command git stash drop stash@{0}.

* **What is the function of ‘git reset’?**

The function of ‘Git Reset’ is to reset your index as well as the working directory to the state of your last commit.

* **How can you fix a broken commit?**

To fix any broken commit, you will use the command “git commit—amend”. By running this command, you can fix the broken commit message in the editor.

* **How to modify commit that had been pushed**

If you need to change the message of an older or multiple commits, you can use an interactive git rebase to change one or more older commits.

The rebase command rewrites the commit history, and it is strongly discouraged to rebase commits that are already pushed to the remote Git repository.

1. Navigate to the repository containing the commit message you want to change.

2. Type git rebase -i HEAD~N, where N is the number of commits to perform a rebase on. For example, if you want to change the 4th and the 5th latest commits you would type:

`git rebase -i HEAD~5`

The command will display the latest X commits in your default text editor:

```
pick 43f8707f9 fix: update dependency json5 to ^2.1.1
pick cea1fb88a fix: update dependency verdaccio to ^4.3.3
pick aa540c364 fix: update dependency webpack-dev-server to ^3.8.2
pick c5e078656 chore: update dependency flow-bin to ^0.109.0
pick 11ce0ab34 fix: Fix spelling.
# Rebase 7e59e8ead..11ce0ab34 onto 7e59e8ead (5 commands)
```

3. Move to the lines of the commit message you want to change and replace pick with reword:
```
reword 43f8707f9 fix: update dependency json5 to ^2.1.1
reword cea1fb88a fix: update dependency verdaccio to ^4.3.3
pick aa540c364 fix: update dependency webpack-dev-server to ^3.8.2
pick c5e078656 chore: update dependency flow-bin to ^0.109.0
pick 11ce0ab34 fix: Fix spelling.

# Rebase 7e59e8ead..11ce0ab34 onto 7e59e8ead (5 commands)
```

4. Save the changes and close the editor.

5. For each chosen commit, a new text editor window will open. Change the commit message, save the file, and close the editor.

```fix: update dependency json5 to ^2.1.1```

6. Force push the changes to the remote repository:

```git push --force branch-name```

* **How to modify commit's author that had been pushed**

For example, if your commit history is `A-B-C-D-E-F` with `F` as `HEAD`, and you want to change the author of `C` and `D`, then you would...

1. Specify `git rebase -i B` (here is an example of what you will see after executing the git rebase -i B command)
    - if you need to edit `A`, use `git rebase -i --root`
2. change the lines for both `C` and `D` from pick to edit
3. Once the rebase started, it would first pause at `C`
4. You would `git commit --amend --author="Author Name <email@address.com>"`
5. Then `git rebase --continue`
6. It would pause again at `D`
7. Then you would `git commit --amend --author="Author Name <email@address.com>"` again
8. `git rebase --continue`
9. The rebase would complete.
10. Use `git push -f` to update your origin with the updated commits.

* **What is cherry pick**

Cherry picking in Git means to choose a commit from one branch and apply it onto another.

This is in contrast with other ways such as merge and rebase which normally apply many commits onto another branch.

1. Make sure you are on the branch you want to apply the commit to.

`git checkout master`

2. Execute the following:

`git cherry-pick <commit-hash>`

N.B.:

1. If you cherry-pick from a public branch, you should consider using

`git cherry-pick -x <commit-hash>`

This will generate a standardized commit message. This way, you (and your co-workers) can still keep track of the origin of the commit and may avoid merge conflicts in the future.

2. If you have notes attached to the commit they do not follow the cherry-pick. To bring them over as well, You have to use:

`git notes copy <from> <to>`
