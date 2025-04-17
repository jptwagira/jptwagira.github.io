---
layout: post
title: git basic commands
date: 2023-02-13 14:24:00
description: Git HOWTOS
tags: code howtos
categories: research datascience
related_posts: true
---

### Git HOWTOS
---

#### 👉 Basic of GitHub Actions Tutorial - Basic Concepts and CI/CD Pipeline with Docker

* Creating CI/CD Pipeline using GitHub Actions for Python Project (Heroku Deployment Example) [here](https://www.youtube.com/watch?v=WTofttoD2xg)
* GitHub Actions Tutorial - Basic Concepts and CI/CD Pipeline with Docker [here](https://www.youtube.com/watch?v=R8_veQiYBjI)
* GitHub Actions Tutorial | From Zero to Hero in 90 minutes (Environments, Secrets, Runners, etc) [here](https://www.youtube.com/watch?v=TLB5MY9BBa4)
* How to resolve "refusing to allow an OAuth App to create or update workflow" on git push [stackoverflow](https://stackoverflow.com/questions/64059610/how-to-resolve-refusing-to-allow-an-oauth-app-to-create-or-update-workflow-on)
* Continuous Integration With Python: An Introduction [Real Python](https://realpython.com/python-continuous-integration/)


#### 👉 How do I fix the white arrow on the folder thing on GitHub even after deleting the .git folder?
You should:

 * git `rm --cached afolder` (no trailing slash), with `aFolder` being the name of the folder in which there was a .git/ subfolder (that you already removed)
 * commit (git commit -m `remove nested Git repository reference`) add (git add aFolder)
 * commit again (git commit -m `Import aFolder content`) and push
 * You should now see aFolder content in your GitHub repository. more details [here](https://stackoverflow.com/questions/66523079/how-do-i-fix-the-white-arrow-on-the-folder-thing-on-github-even-after-deleting-t)


#### 👉 Moving a sub-directory to a new repo with histroy
* check out the tutorial [here](https://www.youtube.com/watch?v=BSVkmpB8M-k)
```.sh
mkdir code
cd code/
git clone https://github.com/jptwagira/p-reconstruction.git
cd p-reconstruction/
git remote rm origin
git filter-branch --subdirectory-filter time-residuals -- --all
mkdir ../p-time-residuals
mv * ../p-time-residuals/
mv .git/ ../p-time-residuals/
cd ../p-time-residuals/
git remote add origin https://github.com/jptwagira/p-time-residuals.git
git pull origin main --allow-unrelated-histories
git push origin main
```

#### 👉 Useful Git Links

* Complete list of all git commands [here](https://git-scm.com/docs)
* Become a git guru from atlassian.com [here](https://www.atlassian.com/git/tutorials)
* Getting Started With GitHub, Part 3: Creating a Read Me File in Markdown [here](https://www.youtube.com/watch?v=yXY3f9jw7fg)
* A Visual Git Reference [here](https://marklodato.github.io/visual-git-guide/index-en.html?no-svg#:~:text=git%20checkout%20HEAD%20%2D%2D%20files,stage%20and%20the%20working%20directory.)
* Git Internals by John Britton of GitHub - CS50 Tech Talk [here](https://www.youtube.com/watch?v=lG90LZotrpo)
* Git MERGE vs REBASE [here](https://www.youtube.com/watch?v=CRlGDDprdOQ)
* Complete Guide to Open Source - How to Contribute [here](https://www.youtube.com/watch?v=yzeVMecydCE)
* Git & GitHub Tutorials [here](https://www.youtube.com/watch?v=xAAmje1H9YM&list=PLeo1K3hjS3usJuxZZUBdjAcilgfQHkRzW)
* GitGuide: GitHub in IceCube [here](https://github.com/icecube/icecube.github.io/wiki/GitGuide%3AGitHub-in-IceCube)
* IceCube GitHub Development [here](https://github.com/icecube/icecube.github.io/wiki)
* IceCube Developer Policy [here](https://github.com/icecube/icecube.github.io/wiki/DeveloperPolicy)
* Contributing to NumPy - Development process - summary [here](https://numpy.org/devdocs/dev/index.html)
* Git configuration [here](https://numpy.org/devdocs/dev/gitwash/configure_git.html)
* How To Compare Two Git Branches [here](https://devconnected.com/how-to-compare-two-git-branches/)
* Git Branching - Rebasing can be found [here](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
* Git Clone Branch – How to Clone a Specific Branch @freecodecamp [here](https://www.freecodecamp.org/news/git-clone-branch-how-to-clone-a-specific-branch/)
* When to use ‘Git Rebase’ explained [here](https://medium.com/@harishlyadav/when-to-use-git-rebase-explained-3c8192cba5c7) by Harish Yadav @medium

* A framework for managing and maintaining multi-language pre-commit hooks [here](https://pre-commit.com/)


* 👉 Setting Up Git on Systems

```.sh
git config --list to check configuration
git config --global user.name "First Last"
git config --global user.email "email"
git config --global merge.tool "vimdiff"
git config --global core.editor "vim"

```

* 👉 Useful Git & SVN commands

```.sh
git checkout "file": restore
git checkout "branch name"
git checkout "commit ID"
git log --oneline
git branch -a
svn status
svn diff
svn log --limit 10
```

* 👉 Checkout a single file to a specific commit
```.sh
git checkout <COMMIT#> <path/to/the/messed/up/file>
```

* 👉 Check the difference between branches A and B
```.sh
git diff branch1..branch2
git diff branch1...branch2
git log branch1..branch2
git diff branches/directreco..origin/stable
git diff origin/stable..branches/directreco
git diff master..feature -- <file>
git diff --color-words
git diff --color-words branch1..branch2
git diff --color-words commit1..commit2
git diff branch-A branch-B
git diff commit1 commit2 file
```
 [here](https://stackoverflow.com/questions/3338126/how-do-i-diff-the-same-file-between-two-different-commits-on-the-same-branch)

* 👉 How to build icetray branch on cluster on cluster by git clone!

```.sh
mkdir icetray
cd icetray
mkdir -p src debug
git clone <url> src
git clone -b "branch name" --single-branch <url> src
condor_submit -interactive -a request_cpus=N
eval $(/cvmfs/icecube.opensciencegrid.org/py2-v3.1.1/setup.sh)
cmake ../src -DCMAKE_BUILD_TYPE=Debug
make -jN
```

* 👉 How to Compile a Particular commit

```.sh
git checkout "branch name"
git log --oneline
git checkout 7a8f31f
condor_submit -interactive -a request_cpus=4
eval $(/cvmfs/icecube.opensciencegrid.org/py3-v4.1.1/setup.sh)
cd ~/icetray/
git log --oneline
mkdir debug / cd debug
cmake ../src
make -j4
```

* 👉 Contributiong to a branch!

```.sh
mkdir icetray
cd icetray
mkdir -p src debug
git clone <url> src
git clone -b "branch name" --single-branch <url> src
```
