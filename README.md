                                         ### Welcome to Git Docs

# What's Git?

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

### Configuring Git
When you come to a bank for the first time and ask to store your money there, they give you a bunch of paperwork to fill out. Before you can use banking services, you have to register with the bank. Git wants you to do the same (register with Git) before you start using a repository.

To tell Git who you are, run the following two commands:

# git config --global user.name "Karthick Krishnaswamy"
# git config --global user.email "karthicbe1@gmail.com"

Since you'll see the output from many Git commands in the terminal, it's best to have some pretty colors for the output. To turn on code highlighting, just run the following command:

# git config --global color.ui true

The last basic configuration command will let you view your Git configurations. Running this command is the same as asking for a copy of your contract:

# git config --list
user.name=karthick krishnaswamy
user.email=karthicbe1@gmail.com
color.ui=true

Starting a New Local Repository with Git

The "init" command stands for initialize. Once you run "git init", Git will initialize a hidden directory called ".git" in the project's root directory. 

# git init test
Initialized empty Git repository in /home/kthiarck/Documents/Devops/git_test/test/.git/

You'll run the command "git status" quite often. It's the same as calling a bank administrator to check if your things arrived or if anything has been moved to a different vault.

# git status
On branch master
Initial commit
nothing to commit (create/copy files and use "git add" to track)


Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/karthicbe1982/karthick.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
