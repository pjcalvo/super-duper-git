# Super Duper Git

## Introduction

This repository is meant to be a practical hands on guide that will help you get throught the `learning git` workshop. 

In this document you will find the entire list of commands that we will use during the workshop along with a short explanation in case you need to come back.

If you find this document confusing or not up to date, please reach out to me and I will kindly adjust the details.

### Notes

During the workshop we will focus mostly on understanding the commands using the [Git CLI](https://git-scm.com/downloads) - _command line interface and try to avoid as much possible the GUI - _graphic user interface_ clients, for the following reasons:

* The Git CLI is a standard multi-platform software, which means that not matter which operation system you are running in you will always be able to run the same commands. While most of the GUI are constrained to operation systems, and could present features on different ways depending on the running environment.
* The Git CLI is actually a very fast and compact sofware. This makes it more convenient when working with larger files or large amount of files at the same time. On the other hands, the performance and size distribution of modern GUI would vary depending on the set of features and maturity of the sofware.
* Each Git GUI client has it's own ways of running and presenting the status of a git project, hidding the under hood mechanics of the process. This could means that the process might be simpler in some of the cases, but not understanding the process is always a constraint when dealing with problems on repositories.
* When dealing with repository problems it is more likely to find solutions online if we are able to present the git commands that we are executing rather than sending the actions executed on a specific GUI.
* Finally, and very subjetive, even when the CLI might appear intimidating at the beginning it is pretty much very simple to use and most of the developers now day rely on it rather than having a preffered GUI.

All these do not means that GUIs are bad, totally the opposite most of them include a rich set of features that help us simplify some processes that require extra eye care and visualizing it on a bigger UI is simpler, such as understanding changes and dealing with conflicts. My recommendation is always to have a GUI you can use in some specific cases, but try to avoid it as much as possible and instead use the CLI commands.

Examples of powerful git GUIs:

* [Git Lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) Recommended cause it integrates with the development IDEs 
* [Kraken](https://www.bing.com/search?q=kraken+git&cvid=cb41a3c24b4f4515871bd997301cb44a&aqs=edge.0.0l9j69i11004.2423j0j1&FORM=ANAB01&PC=U531)


## Git Basics

### What is git?

Git is a open source 'distributed' 'version control system' used widely and mostly in 'development'. In human readable language it means that git facilitate 'teams' to keep historical versions of the same files. To simplify it even further, it works similar to how google drive, dropbox and other version control system works but with two big differences: 

* Changes are not saved automatically, instead they are imperatively syncronized.
* Every new version includes all the changed and non-changed files within a git repository.

![git-working](https://www.git-scm.com/book/en/v2/images/snapshots.png)

Everytime we make a new `commit` to the git history, an full snapshot is taken that reflects the state of the repository. This principle helps us easily switch back and forth in versions, and git is smart enough to deduce which files hasn't changed and therefore it only 'presents' those which present a new change.

### Are there other options?

There are many similar systems as Git, but nowdays and for the last decade and a half git has been the most used version control. Among it's competitors we can find CVS, Subversion and Perforce.

## What do I need to know first?

`/.git` folder

Git works at a folder level, meaning that every file within the specified folder will be tracked. In order to accomplish this git uses a specific hidden folder called `.git` which includes configuration, hooks, logs, and other details about the git repository.

It is important to know that git _does not track folders, and instead works per file_, which means that if we create an empty folder git wouldn't recognize it as part of the project until a first file is added to it.

`.gitignore`

Sometimes we don't want to track some files within a project, for example dependencie libraries (which can be installed on demand) or files containing secrets (such as passwords or tokens). Git does provide a very easy to use mechanism for this called `.gitignore` which is a file that contains fixed names or blob patterns of directories or files that we will want to explicitly skip, for example:

* `node_modules`: will igore all files or folders named node_modules.
* `**.bin`: will ignore all files ending in .bin on any subfolder
* `src/*.exe`: will ignore any .exe file inside src

`.gitkeep`

Sometimes we also want to keep a folder structure as part of git. The accepted community way of doing this is by adding this file inside the folder that we want to preserve.

## Getting started commands

`git config` is the command used in Git to set or get configuration options for a specific repository or globally for all repositories on a user's system.

```bash
git config
git config --local
```

`git init` is a command used to initialize a new Git repository. When you run git init in a directory, it creates a new .git subdirectory in that directory, which contains all the necessary Git metadata for version control.

```bash
git init
ls -la
git config --local -l
git config user.name "Pablo Abstracta"
```

```bash
git remote get-url --all origin
git remote set-url origin https://github.com/pjcalvo/super-duper-git
```

`git clone` is the command to create a copy of an existing Git repository on your local machine. When you run git clone, it copies the entire repository, including all its files, commit history, and metadata.

_Note_: Keep in mind that depending on the repository setting and organization security policies you will have to choose between https or ssh to clone the repository. One uses authentication while the other one uses ssh keys to access the repository. SSH is more popular theses days.

```bash
rm -rf .git
git clone https://github.com/pjcalvo/super-duper-git
cd super-duper-git
git remote get-url --all origin
```

## Snapshoting (changing)

In Git, there are several stages in which changes are saved and tracked before they become part of the permanent history of the repository. 

1) These stages include the working directory. Where we make changes to a file
2) The staging area (also known as the index). Still local, changes could be lost if not added to the repository.
3) And the repository itself. Permanent changes are done on this stage.

### Commands

`git status` is a command used  to show the current status of the repository. This command is our best friend when discovering changes in the working git project. These changes could be:

1. Changes made to the files in the repository since the last commit.
2. Untracked files that have not yet been added to the repository.
3. Branch and commit information, including the current branch you are on.
4. Any files that are staged for commit.

```bash
git status
touch newfile.txt
echo line1 >> newfile.txt
git status
```

`git add` is the command used to add changes made to files in the repository to the staging area, also known as the index.

```bash
git add newfile.txt
git status
touch newfile2.txt && touch newfile3.txt
git add .
git status
```

`git diff` is the command to show the differences between different versions of files in the repository.

```bash
git diff
echo line2 >> newfile.txt
git diff
rm -rf newfile.txt
git diff
```

`git commit` is the command used to save changes made to files in the repository as a new commit.

```bash
git commit -m 'this is a nice commit'
```

`git log` is the command used in the Git version control system to show the commit history of a repository.

```bash
git log
```

`git show` is useful for reviewing the changes made in a specific commit and understanding how the repository has evolved over time. You can use git show to view the changes made in a recent commit or to compare the changes made in different commits to identify bugs or other issues.

```bash
git show de4c631e312a152ec14289838551030704b634a4
```

`git reset` is a command used to undo changes to the repository. It is a powerful command that can be used to unstage changes, reset the repository to a previous state, or delete commits.

```bash
touch newfile2.txt
git add .
git status
git reset 
git add .
git commit -m 'some other commit'
git log
git reset --soft HEAD~1
git log
git add .
git commit -m 'more commits'
git log
git reset --hard HEAD~1
git log
```

`git restore` git restore is another undo changes to files in the working directory. It is similar to git reset, but it only affects the working directory and does not modify the staging area or the commit history.

```bash
echo somechanges >> README.md
git status
git restore README.md
```

## Branching

A branch is a separate line of development in a software project. It is a copy of the codebase that diverges from the main or master branch to allow developers to work on new features, bug fixes, or experiments without affecting the stability of the main codebase.

`git branch` is the command that will allow us to see and manipulate branches in our workspace.

```bash
git branch -a
git branch -l
```

`git checkout` is the command used to switch between different branches or to navigate between different commits within a branch.

```bash
git checkout this-branch
git status
git checkout -
git status
```

```bash
git checkout -b new-branch
git checkout -
git branch -D new-branch
git branch -a
```

## Working with the origin

`git fetch` is used to download changes from a remote repository to a local repository.

```bash
git checkout this-branch
# changes
git fetch
ls
```

`git pull` is used to update a local repository with changes from a remote repository. It combines two other Git commands: git fetch and git merge.

```bash
git pull
ls
```

In summary `git fetch` retrieves the latest changes from a remote repository without modifying the local working directory. In contrast, `git pull` not only retrieves the changes but also automatically merges them with the local branch, potentially resulting in modifications to the local working directory

`git push` is the command that is used to upload local changes to a remote repository. Every change we have staged (commits) will be pushed to the repository

```bash
git checkout -b new-branch-<yourinitials>
git commit -m 'my first commit' --allow-empty
git push
# error
git push --set-upstream origin new-branch-<yourinitials>
git fetch
git branch -a
```

## Merging and rebasing

![rebase-merge](https://jeffkreeftmeijer.com/git-rebase/git-rebase.png)

`git merge` is used to integrate changes from one branch into another branch. It is used to combine two or more branches into a single branch.

```bash
# changes
git checkout main
git pull
git checkout -
git merge main
ls
```

`git rebase`

```bash
# changes
git checkout main
git pull
git checkout -
git rebase main
ls
```

## Exercice

1. Initialize a new Git repository (empty).
2. Create a new file in the repository and add some content to it.
3. Use the git status command to check the status of the repository and see which files have changed.
4. Add the new file to the stage.
5. Create another file and add more content
6. Add the new file to the stage.
7. Create a commit with the message 'my first commit'
8. Try to run push (will fail)
9. Send me a screenshot of `git show`
