[Ansible Install & Config](https://karthicbe1982.github.io/ansible_docs/).

[Ansible playbook](https://karthicbe1982.github.io/ansible_roles/).

# Welcome to Git Docs

## What's Git?

Git is a distributed version control system (DVCS). "Distributed" means that all developers within a team have a complete version of the project. A version control system is simply software that lets you effectively manage application versions. Thanks to Git, you'll be able to do the following:

    Keep track of all files in a project
    Record any changes to project files
    Restore previous versions of files
    Compare and analyze code
    Merge code from different computers and different team members.

These capabilities listed above don't tell how Git actually works, however. In all its complexity, Git works quite simply: you first need to create a local repository in your project's root directory (folder). Afterwards, Git can track project files and directories and add them to the repository. You may be thinking, "Not again! We're talking about a repository now?"

A repository is just a directory (a folder) in your project's root directory. (Throughout the entire article we'll use the term directory, not folder.) You can't see repositories in your filesystem as they're hidden. But you can still see a repository in your code editor or IDE:

In the real world, you can't have exactly the same stuff at home and in a storehouse. If your things disappear from home (God forbid!), you'll be able to recover copies or clones (at best) from a storehouse. And you'll still lose some valuables (the original things). With GitHub or BitBucket, however, it's a different story.

Remote storehouses (repositories like GitHub or BitBucket) store exactly the same code that you have in your local repository (on your home computer). If your code disappears from your local repository, you can restore absolutely the same code from a remote repository. A remote repository also serves as a central hub to which members of a web development team can connect to access project code

## Configuring Git
When you come to a bank for the first time and ask to store your money there, they give you a bunch of paperwork to fill out. Before you can use banking services, you have to register with the bank. Git wants you to do the same (register with Git) before you start using a repository.

To tell Git who you are, run the following two commands:

    $ git config --global user.name "Karthick Krishnaswamy"
    $ git config --global user.email "karthicbe1@gmail.com"

Since you'll see the output from many Git commands in the terminal, it's best to have some pretty colors for the output. To turn on code highlighting, just run the following command:

    $ git config --global color.ui true

The last basic configuration command will let you view your Git configurations. Running this command is the same as asking for a copy of your contract:

    $ git config --list
user.name=karthick krishnaswamy
user.email=karthicbe1@gmail.com
color.ui=true

Starting a New Local Repository with Git

The "init" command stands for initialize. Once you run "git init", Git will initialize a hidden directory called ".git" in the project's root directory. 

    $ git init test
Initialized empty Git repository in /home/kthiarck/Documents/Devops/git_test/test/.git/

You'll run the command "git status" quite often. It's the same as calling a bank administrator to check if your things arrived or if anything has been moved to a different vault.

    $ git status
      On branch master
      Initial commit
      nothing to commit (create/copy files and use "git add" to track)


## Staging Files with Git

To let Git track files for a commit, we need to run the following in the terminal:

    $ git add my_new_file.txt

    $ git add my-file.ts another-file.js new_file.rb

    $ git add .

The option "--all" tells Git: "Find all new and updated files everywhere throughout the project and add them to the staging area." Note that you can also use the option "-A" instead of "--all". Thanks to this simple option, "-A" or "--all", the workflow is greatly simplified.

    $ git add --all

Git can also take things out of its basket by removing files from the staging area. To remove files from the staging area, use the following command:

    $ git rm --cached my-file.ts

## Committing Changes to Git

To commit to a repository, use the "commit" command. Next, pass the "commit" command the "-m" option, which stands for "message". Lastly, type in your commit message. We wrote "Add three files" for our example, but it's recommended that you write more meaningful messages like "Add admin panel" or "Update admin panel". Note that we didn't use the past tense! A commit message must tell what your commit does – adds or removes files, updates app features, and so on.

    $ git commit -m "Add three files"

how can we add modified files to the staging area and commit them at the same time. Git provides the following super command:

    $ git commit -a -m "Do something once more"

To Remove the File before change or Un-tracked 

    $ git checkout file

## Reset

Reset current HEAD to the specified state ( It wont capture any log "git log")

    Soft ----> Will reset to Stage area
    $ git reset --soft SSA ID

    Mixed ----->  Will reset to Untracked area
    $ git reset --mixed SSA ID

    HARD ---> Will delete the file from working directory 
    $ git reset --hard SSA ID

## Remove or Delete Un-tracked file

    $ git clean -df 
    $ rm -rf

## Git Commands for Working with Branches

The reason why we use branches lies on the surface. If you have a stable, working application, you don't want to break it when developing a new feature. Therefore, it's best to have two branches: one branch with a stable app and another one for developing features. Then again, when you complete a feature and it seems to be working, some bug may still be there. And bugs must not appear in a production-ready version. Thus, you'll want to have another branch for testing.


That's it: one command, "branch", will ask Git to list all branches

    $ git branch

The "branch" command creates a new branch with the name we gave it: "user-profile

    $ git branch user-profile

Let's run the "git branch" command once more:

The output will be the following:

    $ git branch
     *master
      user-profile

you'll need to use "checkout" to switch 

    $ git checkout user-profile

Switched to branch 'user-profile'". Let's run "git branch" once more to prove that:

     master
    *user-profile

## Merge 

Once the task done on user-profile , we have to update  on master branch changes made in user-profile

    $ git checkout master

    # git merge user-profile

Delete the branch

    # git branch -d user-profile

## Rebase

Before megre , we have to do rebase from master

    $ git checkout master

    $ git rebase master app

## Stashing your work

The git stash command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy.

    $ git status

## Re-applying your stashed changes

Popping your stash removes the changes from your stash and reapplies them to your working copy

    $ git stash pop

Alternatively, you can reapply the changes to your working copy and keep them in your stash with 

    $ git stash apply

Stashing untracked or ignored files

By default, running git stash will stash:

    changes that have been added to your index (staged changes)
    changes made to files that are currently tracked by Git (unstaged changes)

But it will not stash:

    new files in your working copy that have not yet been staged
    files that have been ignored


Adding the -u option (or --include-untracked) tells git stash to also stash your untracked files:

    $ git stash -u

Managing multiple stashes

    $ git stash list

To provide a bit more context, it's good practice to annotate your stashes with a description, using 

    $ git stash save "message":

You can choose which stash to re-apply by passing its identifier as the last argument, for example:

    $ git stash pop stash@{2}

    $ git stash show -p

If you decide you no longer need a particular stash, you can delete it with 

    $ git stash drop stash@{1}

Or you can delete all of your stashes with

    $ git stash clear

    $ .gitignore

      1.    tracked - a file which has been previously staged or committed;
      2.    untracked - a file which has not been staged or committed; or
      3.    ignored - a file which Git has been explicitly told to ignore.

Global Git ignore rules

    $ git config --global core.excludesFile ~/.gitignore



