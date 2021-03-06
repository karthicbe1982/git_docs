Return to [**devops**](https://karthicbe1982.github.io/devops/)

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
      user.name=Karthick Krishnaswamy
      user.email=kthiarck@gmail.com
      color.ui=true


Starting a New Local Repository with Git

The "init" command stands for initialize. Once you run "git init", Git will initialize a hidden directory called ".git" in the project's root directory. 

    $ git init test
      Initialized empty Git repository in /tmp/project/.git/
    

You'll run the command "git status" quite often. It's the same as calling a bank administrator to check if your things arrived or if anything has been moved to a different vault.

    $ git status
    # On branch master
    #
    # Initial commit
    #
      nothing to commit (create/copy files and use "git add" to track)
  


## Staging Files with Git

To let Git track files for a commit, we need to run the following in the terminal:

    $ git add my_new.txt

    $ git add my-file.ts another-file.js new_file.rb

    $ git add .
    
    $ git status
    # On branch master
    #
    # Initial commit
    #
    # Changes to be committed:
    #   (use "git rm --cached <file>..." to unstage)
    #
    #	new file:   my_file.txt
    
The option "--all" tells Git: "Find all new and updated files everywhere throughout the project and add them to the staging area." Note that you can also use the option "-A" instead of "--all". Thanks to this simple option, "-A" or "--all", the workflow is greatly simplified.

    $ git add --all

Git can also take things out of its basket by removing files from the staging area. To remove files from the staging area, use the following command:

    $ git rm --cached my-file.txt
      rm 'my_file.txt'
 
    $ git status
    # On branch master
    #
    # Initial commit
    #
    # Untracked files:
    #   (use "git add <file>..." to include in what will be committed)
    #
    #	my_file.txt
      nothing added to commit but untracked files present (use "git add" to track)


## Committing Changes to Git

To commit to a repository, use the "commit" command. Next, pass the "commit" command the "-m" option, which stands for "message". Lastly, type in your commit message. We wrote "Add three files" for our example, but it's recommended that you write more meaningful messages like "Add admin panel" or "Update admin panel". Note that we didn't use the past tense! A commit message must tell what your commit does – adds or removes files, updates app features, and so on.

    $ git commit -m "First commit"
      [master (root-commit) b05fb74] first commit
      1 file changed, 1 insertion(+)
      create mode 100644 my_file.txt


how can we add modified files to the staging area and commit them at the same time. Git provides the following super command:

    $ git commit -am "Do something once more"

To Remove the modified file before change or Un-tracked 

    $ git checkout file
    
    $ cat my_file.txt 
      First commit
      second commit
      third commit
      fourth commit  <---------- Added 
      
    $ git status
    # On branch master
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #	modified:   my_file.txt
    #
      no changes added to commit (use "git add" and/or "git commit -a")

    $ git checkout my_file.txt
 
    $ cat my_file.txt 
      First commit
      second commit
      third commit

    $ git status
    # On branch master
      nothing to commit, working directory clean
 
    
## Reset

Reset current HEAD to the specified state ( It wont capture any log "git log")

    Soft ----> Will reset to Stage area
    $ git reset --soft SHA ID

    Mixed ----->  Will reset to Untracked area
    $ git reset --mixed SHA ID

    HARD ---> Will delete the file from working directory 
    $ git reset --hard SHA ID

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

By default, running "git stash" will stash:

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



## Viewing the Commit History

When you run git log , you should get output that looks something like this:

     $ git log
       commit ca82a6dff817ec66f44342007202690a93763949
       Author: Scott Chacon <schacon@gee-mail.com>
       Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the version number


A huge number and variety of options to the git log command are available to show you exactly what you’re looking for. Here, we’ll show you some of the most popular.

One of the more helpful options is -p or --patch, which shows the difference (the patch output) introduced in each commit. You can also limit the number of log entries displayed, such as using -2 to show only the last two entries.

     $ git log -p -2

This option displays the same information but with a diff directly following each entry. This is very helpful for code review or to quickly browse what happened during a series of commits that a collaborator has added. You can also use a series of summarizing options with git log. For example, if you want to see some abbreviated stats for each commit, you can use the --stat option:

     $ git log --stat

As you can see, the --stat option prints below each commit entry a list of modified files, how many files were changed, and how many lines in those files were added and removed. It also puts a summary of the information at the end.

Another really useful option is --pretty. This option changes the log output to formats other than the default. A few prebuilt options are available for you to use. The oneline option prints each commit on a single line, which is useful if you’re looking at a lot of commits. In addition, the short, full, and fuller options show the output in roughly the same format but with less or more information, respectively:

     $ git log --pretty=oneline
       ca82a6dff817ec66f44342007202690a93763949 changed the version number
       085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7 removed unnecessary test
       a11bef06a3f659402fe7563abf99ad00de2209e6 first commit

You may be wondering what the difference is between author and committer. The author is the person who originally wrote the work, whereas the committer is the person who last applied the work. So, if you send in a patch to a project and one of the core members applies the patch, both of you get credit — you as the author, and the core member as the committer. We’ll cover this distinction a bit more in Distributed Git.

The oneline and format options are particularly useful with another log option called --graph. This option adds a nice little ASCII graph showing your branch and merge history:

     $ git log --pretty=format:"%h %s" --graph
     * 2d3acf9 ignore errors from SIGCHLD on trap
     *  5e3ee11 Merge branch 'master' of git://github.com/dustin/grit
     |\
     | * 420eac9 Added a method for getting the current branch.
     * | 30e367c timeout code and tests
     * | 5a09431 add timeout protection to grit
     * | e1193f8 support for heads with slashes in them
     |/
     * d6016bc require time for xmlschema
     *  11d191e Merge branch 'defunkt' into local




