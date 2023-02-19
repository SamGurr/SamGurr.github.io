---
layout: post
title: Time to git started
date: '2023-02-18'
categories: Protocols
tags: git workshop NOAA github RClub
---

# Before we 'git' going..

* start a git account

* download a user interface to interact with github from your command line

	- git

	- github user interface

* email your github account ID to samuel_gurr@noaa.gov to be added as a collaborator to the repository 'RClub' and accept the invitation to be a collaborator (you will get an email notification)

	- NOTE:  git appears same as raw shell lfor using linux commands whereas the github UI is an application-like interface the following workshop uses commands for a git workflow that can be translated to the UI if prefered  

## objective:

* initiate team-based version control using our collaborative 'RClub' resository!

	- use basic linux commands to navigate your computer

	- use a handful of main git commands to clone, edit, and add to the collaborative 'RClub' repository

# Let's 'git' it started!
----

### objective:

* apply a few linux commands on command line (git) to navigate your directory and create, move, and delete files

* 'clone' a preestablished github repository to your own laptop

* learn how the clone process differs if you are or are not a assigned collaborator for the repository

**Below are steps supplemented with color-coded <span style="color:red">linux</span> and <span style="color:green">git</span> commands**

### Clone the RClub repo from git command line

(1) Open git on your computer

(2) Use <span style="color:red">linux</span> commands to navigate to a directory where you want the 'RClub' respository to live. *You are now ready to <span style="color:green">git</span> the repository*

	- NOTE: the 'RClub' repository is already active and on github. you can  establish a new repository from command line (example tutorial [here](https://kbroman.org/github_tutorial/pages/init.html)) though we will not do this today

* <span style="color:red">cd</span> to return or call your home directory

```
cd
```

* nativigate forward

```
cd dir (where dir = directory name with '/' dividing each subseqent folder)
```


* navigate backward

	- NOTE:  repeat ../ for each folder preceeding

```
cd ../
```

* <span style="color:red">ls</span> to read the directory listing (what is in the current directory?)

```
ls
```

	- NOTE: repository is just a jargony word for a folder, treat this as you would any project folder

(3) *optional* make, move, and delete directories

* copy the file using <span style="color:red">cp</span>

```
cp dir/filename newdir
```

* move the file (same a the 'cut' command on PC, file is not longer at original location) using <span style="color:red">mv</span>

```
mv dir/filename newdir
```
* **Important**: below are commands for deleting files. Please be cautious here as **deleting from command line is permanent and non-recoverable when you are not in a git repository**. In this exercise you are essentially navigating your file explorer with admin rights - use the following commands wisely.

* CAUTION: delete a **file** using <span style="color:red">rm</span>

```
rm filename
```

* CAUTION: delete a **directory** (-r means including EVERYTHING in it!) as <span style="color:red">rm -r</span>

	- NOTE:  -r means recursive, all contents within the dir are called for deletion

```
rm -r dir
```

* The asterisk is a powerful tool <span style="color:red">*</span> - when placed before or after a common filename string, its purpose is to call all content with that string

* example: you are in a data folder with excel files titled 2022_temp_1.xls, 2022_salinity_2.xlsx, 2022_pH_5.csv, 2021_temp_2.xlsx and you want to move *only 2022 files* to a different folder. From command line you run:

```
mv 2022* <dir destimation>
```

* the asterisk calls all files in the folder with the common filename string '2022' regardless of the string thereafter, and excluding the single file that reads '2021'

(4) Open the internet page for the repository https://github.com/SamGurr/RClub - remember you are now a collaborator on this repo!

(5) click on the green box named Code. This will default to the HTTPS option for cloning the repository as https://github.com/SamGurr/RClub.git. Copy it!

(6) in your git window, clone the repository using <span style="color:green">git clone</span> as the following command

*Important!: the following steps will add all content in 'RClub' **including the head folder 'RClub'**, therefore you do not have to name a folder for it.*

For example, you can initiate this process in a directory as simple as Documents or Documents/Github_repositories  or Documents/My_Projects.
The choice is yours and will have zero impact on the collaborative repo - this is where 'RClub'  will live *on your computer for you only*

```
git clone https://github.com/SamGurr/RClub.git
```

* you will see a it load into your git command line, should reach 100% fairly quick (~10-20 seconds)

(7) Great work! You now have RClub on your laptop!
 In other words, you *'git' the power*...

(8) Lets look at it using the linux commands learned above (use cd and ls)

* you can also look at the folder contents using your file explorer

*"With great power comes great responsibility" -Uncle Ben (Stan Lee)*
 We all have master rights to this repository meaning that it can easily spiral to data conflicts when one version is behind/past another.
These issues worsen as teams grow and become more productive. Seems counter-intuitive right? Working in this informal setting with non-critical data
(this RClub repository) allows us to troubleshoot, learn, and decide upon what fits best for our current and future teams.

In the following steps, we will learn about forks and branches. These are essential aspects of collaborative workflows using git
to better manage large and productive teams!

# Cracking to code of Branches and Forks
----

### objective:

* to learn the basics of forks and branches and how they may or may not apply to a collaborative workflow

You're likely saying to yourself, *'git' outta 'ere with this jargon!*, I'll briefly touch on these useful tools. As mentioned above, you are all collaborators on the 'RClub' repository with full contribution and collaboration rights - one can smell the potential for trouble here with failed pushes, overwritten merges, and temporary distress oh my!

	- NOTE: though we will not touch on this today, version control allows us to revert back to **any** commit for a given repo - meaning that any version of a file can be recovered


#### Definitions:

**fork** - a **duplicated** and **independent** version of from the original repository **up to the time it was forked**. A forked repository contains all the contents including the branches,
however all edits to a forked respository have no effect on the original.

- useful when you want another researchers code for your own use without collaborating. The intent here is to split for an independent project/edits that may never reunite with the parent/origin (main) repository

- example: website templates, code and mock data, etc. open data is cool right!

	- alternative definition: a 3-4 pronged utencil for formally transporting nutrients as opposed to the fingers that have well adapted for this task

**branch** - think **under construction** or **work in progress**, the branch is akin to a manuscript with track changes on where the parent/origin is a separate document that is managing changes.
In other words, the branch mimics the parent/origin but its purpose is to prevent direct integration of change to the master repository without a stamp of approval from the manager(s)

- version control with local versus remote repositories

- useful for collaborative workflow in large teams when edits are created on a particular feature with the intent to manage what is integrated to the parent/origin - occasionally a branch can be named for a particular task - the start of a branch can also occur at a particular version or prior commit to the repository

	- alternative definition: a tree's fingers of which a tree's *forks* would be much more appropriate in our modern age (review alt def of fork)

We have a <span style="color:green">branch</span> remote branch 'teamwork' that was first established locally before pushed as a remote branch. This branch is up-to-data with the main branch and you will receive it when you clone the repository

* a 'teamwork' branch (<span style="color:green">-b</span>) was created in for the Rclub repository by using the commands below - each shown with descriptions in []

```
(do NOT run these - a remote branch was already established for our use)

git branch teamwork [create local branch]
git branch [view your local branches]
git switch teamwork [switch branch to new branch]
git push -u origin teamwork [pushes the new local branch as a remote branch, -u facilitates tracking]
git branch -v [view commits/changes ahead and behind the remote branch, we can use this call because of the -u tracking when first establishing teamwork as remote branch]
```

(1) Knowing we have a branch for 'teamwork' and a 'main' branch - lets look at these

 use <span style="color:green">git branch</span> to see what branch you are in

```
git branch
```

* *the output will list all existing branches with your highlighted/bold.

	- NOTE:  Notice that the branch you are in  is also shown in () at the end of our git command directory

(2) Navigate to the teamwork branch

 use <span style="color:green">git switch branchname</span> to switch

```
git switch teamwork
```

# Version control for leading RClub sessions
----

### objective:

* walkthrough version control example as **the weekly tasks for the assigned discussion leader**

* use <span style="color:red">linux</span> commands to view, open, and edit files

	* use default text editors from command line <span style="color:red">nano</span>, <span style="color:red">vim</span>

	* create an alias shortcut to open notepad.exe using <span style="color:red">note</span>

	* create and edit files in RClub (schedule, notes, add documents, etc.)

* use a sequential workflow of <span style="color:green">git</span> commands

	* <span style="color:green">git pull</span> to integrate changes you do not have

	* <span style="color:green">git status</span> to view changes you made

	* <span style="color:green">git add</span> to add your changes to the queue

	* <span style="color:green">git commit</span> to establish a record of your changes

	* <span style="color:green">git push</span> to integrate your changes to the main repository

### View files from command line

* start, read, and edit a file

**there are a few text editors you can use, each have their limitations**

**<span style="color:red">nano</span>** : nano is a default test shell from command line to read and write, though limited in its ease of use. Ex: only arrow keys to navigate, no shortcuts such as Cntrl+C to copy will function

* navigate to the RClub repository and open README.md to see for yourself!

```
nano README.md
```

**<span style="color:red">vim</span>** : another stock text shell, even more cumbersome than nano.

* do the same with vim

```
vim README.md
```

**lets call a better user interface to work in shall we!**

* below we will navigate to our home directory and edit our .bashrc file.  This file contains editable configurations for the use to interact with terminal

* navigate home

```
cd ~/
```

* open .bachrc using nano

```
nano .bashrc
```

* the GNU will open, looks like command line window with option band below.

* click with your cursor in the empty space, add the text below to make an **shortcut** as an **'alias'** to **notepad.exe** which is a default text editor on our PCs

```
alias note='C:/Windows/System32/notepad.exe'
```

* we now have a shortcut to use in terminal/git to open notepad as opposed to the clunky nano and vims!

* close git and reopen to integrate this changes

* type note to open notepad.exercise

```
note
```


#### How read and open text files from command line to save edits

Before getting started, navigate to the teamwork branch (if not there already)

```
git switch teamwork
```



(1) View whole file in command line

* use <span style="color:red">cat</span> to open **the whole file**

*  navigate to RClub directory and look at README.md for example

```
cat README.md
```

* notice this prints directly in command line and is **read only**

* sometimes we may not want to see the whole file whether it is too large or just not of interest. here use a pipe <span style="color:red">|</span> to call in the next command <span style="color:red">head</span> to read only the first 10 lines, you can change the number of lines as you see fit

(2) View start of a file in command line

<span style="color:red">cat</span> to view a text file and <span style="color:red">head</span> to view lines from the start of the file

```
cat filename | head -10
```

* notice this prints directly in command line and is also **read only**

(3) View the end of a file in command line

* use span style="color:red">tail</span>' to call lines from the end of a file

```
cat filename | tail -10
```

*you can now successfully view the content of a text file in command line!*

#### Open text file from command line to edit and save changes

(1) Navigate to directory RClub/sessions/3_3_2023_Git_workshop

* call below depends where your current directory is..

```
cd RClub/sessions/3_3_2023_Git_workshop
```

(2) open a file called yourname_file.txt

* *option 1*: use <span style="color:red">nano</span> to open with nano shell

```
nano yourname_file.txt
```

* *option 2*: use <span style="color:red">note</span> to open using our alias to notepad.exe

```
note yourname_file.txt
```

(3) edit file adding whatever text you desire


(4) save the file

* *option 1*: if you opened using <span style="color:red">nano</span>

			**Cntl+X** to Exit - this will prompt whether to save

			**Y** to save

			**enter** to exit back to commnd line


* *option 2*: if you opened using <span style="color:red">note</span>

		**Cntl+S** to save

		simply exit the page


* use commands you know to see if you successfully made the file and view it in command line!

```
ls  
```

```
cat  yourname_file.txt
```
### Git workflow - *pull-status-add-commit-push*

* we now have a change that was made to the repository, but only our own!

* below is a sequential workflow as best practice for working with git!

#### objective:

* add yourname_file.txt to the teamwork branch online and integrate all changes (everyone else's yourname_file.txt files) to your local branch!

(1) Navigate to the RClub

(2) Use <span style="color:green">git pull</span> to integrate changes on the remote teamwork brnach that you do not have

```
git pull
```

* if there are no changes, it will say it is up to date

	- NOTE: this is the step where merge conflicts may arise, we can work on this in future meetings

(3) Use <span style="color:green">git status</span> to view changes you made. This should dhow the yourname_file.txt in red to indicate is a pending edit that has not been added

```
git status
```

(4) Use <span style="color:green">git add</span> to add your changes to the queue.

```
git add <dir>/yourname_file.txt
```

(5) Use <span style="color:green">git status</span> again. You will now see yourname_file.txt is green because you verified it was a change you want to add

```
git status
```

(6) Use <span style="color:green">git commit</span> with <span style="color:green">-m</span>to establish a record of your changes

```
git commit -m "a message here for your record, requires quotes!"
```

* now if your rerun git status it will tell you there is nothing to add, a commit is a step above meaning that the changes are established to move forward

(7) Use <span style="color:green">git push</span> to integrate your changes to the repository

* <span style="color:green">origin main</span> == to the main repository

* <span style="color:green">origin master</span> == older git repos are called 'master', however ours is 'main' so do not worry

```
git push origin teamwork
```

# Celebrate, you 'git' it!

**WOW! you now integrated a new edit to the teamwork repository. [Check it out on github](https://github.com/SamGurr/RClub/tree/teamwork)**

# But wait! We 'git' to MERGE it with the main!

### online

* pushing from a branch is called a **pull request** to the main branch

* you can see on the RClub page that there are pull requests generated by our cumulative pushes to the remote teamwork branch

* this interfance online allows us to observe where there are conflicts (if any) and merge with the main

- NOTE: if you do this online, make sure to **pull** to your local so that you are up to date

### from command line

* return to the main local branch on your git (now main is your HEAD branch)

```
git switch main
```

* merge your current HEAD branch (main) with the changes in teamwork

```
git merge teamwork
```

* repeat the same workflow

	- git status

	- git add

	- git status

	- git commit -m <your message>

	- git push origin main


# Celebrate.. again!

**your changes to teamwork are not integrated in the main repository.** [Check it out on github](https://github.com/SamGurr/RClub)
