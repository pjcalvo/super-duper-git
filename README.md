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

## Getting started

init
clone


## Snapshoting (changing)

add
status
diff
commit
notes
restore
reset
rm
mv


