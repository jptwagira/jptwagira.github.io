---
layout: post
title: git basic commands
date: 2023-02-13 14:24:00
description: Git HOWTOS
tags: code howtos
categories: research datascience
related_posts: false
---

### Git HOWTOS
---

#### 👉 Basic Concepts and CI/CD Pipeline with Docker

* Github Actions and Continuous Integration [icetray-public](https://github.com/icecube/icetray-public/tree/main) and [skymap-scanner](https://github.com/icecube/skymap_scanner)
* Continuous Integration With Python: An Introduction [Real Python](https://realpython.com/python-continuous-integration/)


#### 👉 Useful Git Links

* GitGuide: GitHub in IceCube [here](https://github.com/icecube/icecube.github.io/wiki/GitGuide%3AGitHub-in-IceCube)
* IceCube GitHub Development [here](https://github.com/icecube/icecube.github.io/wiki)
* IceCube Developer Policy [here](https://github.com/icecube/icecube.github.io/wiki/DeveloperPolicy)

* Complete list of all git commands [here](https://git-scm.com/docs)
* Become a git guru from atlassian.com [here](https://www.atlassian.com/git/tutorials)
* A Visual Git Reference [here](https://marklodato.github.io/visual-git-guide/index-en.html?no-svg#:~:text=git%20checkout%20HEAD%20%2D%2D%20files,stage%20and%20the%20working%20directory.)
* Git & GitHub Tutorials [here](https://www.youtube.com/watch?v=xAAmje1H9YM&list=PLeo1K3hjS3usJuxZZUBdjAcilgfQHkRzW)
* A framework for managing and maintaining multi-language pre-commit hooks [here](https://pre-commit.com/)


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


#### 👉 Setting Up Git on Systems

```.sh
git config --list to check configuration
git config --global user.name "First Last"
git config --global user.email "email"
git config --global merge.tool "vimdiff"
git config --global core.editor "vim"

```

#### 👉 Useful Git & SVN commands

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

#### 👉 Check the difference between branches A and B
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

#### 👉 How to build icetray branch on cluster on cluster by git clone!

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
