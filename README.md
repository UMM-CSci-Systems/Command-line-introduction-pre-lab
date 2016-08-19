# Command Line Introduction pre-lab

Pre-lab for the [Command-line-introduction lab](https://github.com/UMM-CSci-Systems/Command-line-introduction). This lab and pre-lab cover:

* The basics of using the command line and the `bash` shell
* Using a command line editor
* Writing simple `bash` scripts
* Using `git` and Github as tools for managing changes to code

One of the consistent messages we get from alums and employers is that people really need to know how to interact effectively with the command line. It's nice to use nifty GUI tools when they're available, but there are times when the only access you have to a box is via the command line. You might have to `ssh` to a server in the cloud, for example, edit a configuration file with a command line editor, commit and push those changes, and then restart a service. It might be that none of those steps is very hard, but the command line freaks you out it can be a nightmare. Also both `emacs` and `vim` cope fairly gracefully with editing very large files, where many GUI editors don't; we have editing multi-gigabyte text files with both `emacs` and `vim`.

So one of the key goals of this lab is to begin to gain familiarity with the command line and command line editors. One lab won't make you an expert, but hopefully it will be a useful step in helping you feel more competent.

**Table of Contents** 
  - [Tasks to learn](#tasks-to-learn)
  - [Picking a command line editor and starting to learn it](#picking-a-command-line-editor-and-starting-to-learn-it)
  - [The basics of `bash` and Unix command line tools](#the-basics-of-bash-and-unix-command-line-tools)
     - [Exercises](#bash-exercises)
  - [gitting to it](#gitting-to-it)
     - [Exercises](#git-exercises)
  - [What to do](#what-to-do)

## Key tasks

* Pick a command-line editor and start to learn it
* Start reading about 'bash'
* Start reading about 'git'
* Complete a simple group of `bash` exercises
* Complete a simple group of `git` exercises

## Picking a command line editor and starting to learn it

It's enormously useful to know how to use a command line editor for those times when you don't have access to all the nifty windowing stuff that we've grown so happily used to using. Your best options are probably `emacs` and `vim` (or its less sophisticated ancestor `vi` ).  There are many other options, but these two are some of the more popular *powerful* options (I'll outline a few reasons below)

Some people prefer more user-friendly options like `nano` or `pico`, but if you are starting from scratch it is not a bad idea to pick one with a tougher learning curve like `vim` or `emacs`.  They are harder to learn at first, but offer much more powerful options later. Both `emacs` and `vim`, for example, provide powerful macro facilities that let you "record" and "play back" a sequence of keystrokes so you can quickly repeat a complex modification (something you couldn't do with search and replace) numerous times in a large file.

Both Nic and Peter know both `emacs` and `vim`; Nic is likely to (still) use `emacs` these days, while Peter typically uses `vim` now. There are long and drawn out religious wars between fans of the two editors which we will not enter into. We will point out a few differences, however:

* Almost every version of linux or unix comes with `vi` "out of the box". Because of this, `vim` is set to be the default editor in a lot of systems. This alone is reason to know at least the bare basics of `vim` since you're almost guaranteed to find yourself in it at some point, and it would be nice if you could at least save and exit without hurting yourself.
* Emacs is big, which is why it isn't a default part of many small Linux installs. It has a Turing complete scripting language and in many ways was designed to provide an entire "windowing" user environment before we had "real" GUI windowing environments. This obviously cuts both ways – you can use the `elisp` scripting language to do crazy complex customizations and extensions, but we don't know anyone who knows and uses more than a fraction of `emacs`s power.
* `vim` is _modal_ and `emacs` isn't. In `vim` you have different modes; in "normal" mode you can navigate manipulate text, for example, where you need to switch to "insert" mode to just type text. Different people respond to in very different ways to this kind of modality; lots of people (including Peter) don't mind it at all, where it drives Nic crazy.
* `vim` tries to improve efficiency by having the most commonly used navigation keys on the "home row" (the position at which a touch-typist's hands rest).  The arrow-keys still work as expected in `vim` (not necessarily in `vi` however).  Again, some people love this, and some people hate it.

The Internet is awash in materials on both editors:

* The tutorial http://vim-adventures.com/ was fun
* A Wikibook: ["Learning the vi Editor"](https://en.wikibooks.org/wiki/Learning_the_vi_Editor)
* [A tour of Emacs](http://www.gnu.org/software/emacs/tour/)
* [The _Mastering Emacs_ reading guide](https://www.masteringemacs.org/reading-guide)
* [Absolute beginner's guide to emacs](http://www.jesshamrick.com/2012/09/10/absolute-beginners-guide-to-emacs/)
* [Cult of vi vs church of emacs](https://en.wikipedia.org/wiki/Editor_war)

## The basics of `bash` and Unix command-line tools

Unix and Unix-like systems provide an incredibly powerful collection of command line tools for processing and manipulating files and their contents. Over the course of these labs we'll cover what may seem like a _ton_ of command line material, but which will in fact only be a fraction of what's possible.

Many of you will come into this with almost no experience with the Unix command line, while others may already have a fair amount of practice with these tools. Luckily there are a _lot_ of good resources on the Internet to help get us all up to speed. A few tutorials that we think should be helpful:

* ["Learn Enough Command Line to Be Dangerous"](https://www.learnenough.com/command-line-tutorial)
* ["Linux tutorial" by Ryan Chadwick](http://ryanstutorials.net/linuxtutorial/)
* ["BASH Programming - Introduction HOW-TO"](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

These are in roughly decreasing order of "chattiness". The "Learn Enough" tutorial is complete with sidebars and XKCD (relevant) comics, where the "BASH Programming" introduction is from 2000 and much more terse and "business-like"; the Chadwick tutorial is somewhere in between. They also don't cover exactly the same material in the same order; if you find one's coverage of a concept (e.g., pipes) doesn't make a lot of sense, have a look at how it's covered in one of the other tutorials.

Alternatively, if you prefer videos/screencasts, these two series:

* [Linux commands for beginners](https://www.youtube.com/playlist?list=PLT98CRl2KxKHaKA9-4_I38sLzK134p4GJ)
* [Introduction to `bash` scripting](https://www.youtube.com/playlist?list=PLT98CRl2KxKG2RCPkG6EPOA-g1FmLfcZl)

cover essentially the same material, but again in a quite different order and with a different style. (You'll notice that the narrator is using `nano` as their editor – _you_ should be using the editor you choose earlier.) These videos do a pretty good job about starting from the bare minimum, but:

* It's hard to go back and find previous information
* Following along with the video can be a lot slower than following along with text for some people

In order to prepare yourself for this lab, and others that will follow, you should go through one or more of these (or something similar you find on-line that's more to your taste). We don't really care _which_ one you do, but we will expect you to have gone through something like this and made some effort to explore and practice with soem of the basic tools. This is likely to take a few hours (especially if you "play along" at home, which you'll really want to do if you want to _learn_ these concepts and tools), so don't assume you can just bang through one of these in 15 minutes.

We would _strongly_ advise that you go through your tutorial(s) of choice in the lab or at least at a machine that has a terminal program with the bash shell installed so you can try some of these things out as you go along. Most Windows users won't have a version of `bash`, and if you're not sure you almost certainly don't. It's available standard out of box on Macs and Linux boxes; if you have a Mac, look in you `Applications/Utilities` and you'll find it. If you are using windows you can install `cygwin` (https://www.cygwin.com/). You can also using the MacOS `Terminal` program or something like Putty on Windows to `ssh` into a lab box and go through the tutorial that way.

As you are going through the tutorial go through it once in a quick pass and don't worry too much if things don't make perfect sense the first time. If something is not making sense on your second reading, or does not seem to be working correctly **please** ask about it.

The final thing we'll mention here is the `man` command. If during your reading or the lab you run across a command that you aren't familiar with then the `man` command can be your friend. To find out more about a certain shell function simply type

```man function_name_here```

This will bring up a page that (supposedly) describes what that function does. Navigate the man page with the arrow keys and press q to quit back to the command line. Keep in mind that man pages are written by the person or persons who created the function. This means that the man pages throughout the shell vary from extremely technical and detailed to non-existent. If the man page isn't helpful, some simple searching on-line should bring up tons of sites to supplement a confusing `man` page. :exclamation: Be careful, though, as there can be important if subtle differences between different versions of commands, and you're best off using the `man` pages on the system you're using whenever possible.

###<a name="bash-exercises"></a>Exercise (due before the start of lab on Tuesday)

You'll want to start by making a directory to hold your files and subdirectories.  Call that whatever you like-- you're not going to turn it in-- only its contents.  We'll call it the the prelab directory.

In the prelab directory, you are going to be creating a directory called `testing` that contains two files and an empty directory called `more_testing` (More on that down below.)  Your prelab directory should also contain a text file (that you will need to create) named *your_group.member_a.member_b.lab0_prelab.txt* (for example:  `eternal_lettuce.dolanp.lamberty.lab0_prelab.txt`).  That file will contain the answers to the questions I ask below:

You can either construct this directory and file structure by hand using tools like `mkdir` and editors, or you can copy the directory structure from `/home/dolanp/pub/CSci3403/testing` using `cp`. (You'll want to be able to do it both ways, so you might try it both ways as well.)

Everything that follows assumes that you're starting in the directory called `testing`.

The first file is called `testfile1.txt` and contains the following text:

```
I like coding with bash!
Shell scripts are awesome!
```


The file `testfile2.txt` is also contained in `testing` and contains the following text:

```
I'm scared without the safety of Eclipse!
Take me back Java!
```

Remember that the `testing` directory should also contain an **empty** directory named `more_testing`.

Assume all scripts start in the testing directory unless otherwise stated.  Your *your_group_lab0_prelab.txt* file should contain the directory you're in (the `pwd` [Print Working Directory] command will be useful here) after **each** line of the following code:

```
cd /home/dolanp/pub
pushd ~
pushd
```

It should also contain the output of each of the following lines:

```
grep bash testfile1.txt
grep bash testfile2.txt
grep -l bash *.txt
find -type f
find -type d
```

And finally, include the contents of `testfile1.txt` and `testfile2.txt` after the following two lines are executed:

```
sed -i "s_Eclipse_my cuddly IDE_g" testfile1.txt
sed -i "s_Eclipse_my cuddly IDE_g" testfile2.txt
```

##<a name="gitting-to-it"></a>`gitting` to it

We'll use `git` through the course as a way for groups to manage shared project resources (like code) and as the primary means for you to turn in your finished work. Some of you will be familiar with `git` from previous courses, while others will have never used it before. If you've never used `git` before you might want to read https://www.atlassian.com/git/tutorials/
and https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches

####<a name="git-exercises"></a>Exercise (also due before class on Tuesday)

You belong to the organization UMM-CSci3403-F15.  One person in your group should login to Github and go to [https://github.umn.edu/UMM-CSci3403-F15/Prelab-0] which has this file (as you know-- you **are** after all reading this).  Next you should create a fork of this repository and push the text files (and subdirectories) with your answers from above.   Don't forget the your file of the form *your_group.member_a.member_b.lab0_prelab.txt* needs to be in your project's root directory so I can know who is in your group.  Make the name of your branch your group name.

Here is one set of procedures you could follow (there are others):

* Clone the file(s) from the repository using `git clone  https://github.umn.edu/UMM-CSci3403-F15/Lab_0.git` (This will make a subdirectory.  Change the current directory to this subdirectory.)
* Create a new branch `git branch [name_of_your_branch]`
* Switch to that branch `git checkout [name_of_your_branch]`
* Make your changes to the contents.  (This is done on your local computer.)  This is where you make the subdirectories and files (or copy them) from your previous set of exercises.
* Add your new files to the repository using `git add .` while in the root directory of the project,
* commit your changes with the comment "This is my first git commit!" (you can figure this one out), 
* and then push them with `git push -u origin [name_of_your_branch]`.
*  You may want to log into github, go to your new branch, click "Settings", choose the "Collaborators" tab, and add your team-mates to the list.

ALERT! Remember to use `git add` to put your file under version control before you commit. You can use `git status` to see what has changed and needs to be committed.  **ALSO** empty subdirectories won't be added-- so your `more_testing` subdirectory won't be included (even if you try to add it by hand) unless you create a file inside of it.  You can also fork the project 

##What to do

By the start of next lab you should
* Have gone through this entire lab
* Choose an editor and have put some time into learning how to use it
    * Emacs
    * VIM (playing vim adventures counts)
* Finished the tutorial http://www.linuxdoc.org/HOWTO/Bash-Prog-Intro-HOWTO.html
* Completed the [Bash Exercises](#bash-exercises)
* Completed the [git Exercises](#gitting-to-it)
