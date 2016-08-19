# Command-line-introduction pre-lab

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
  - [Learning bash](#learning-bash)
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

##Learning bash

In just a moment I am going to ask you to do a tutorial.  In a few places that tutorial makes some assumptions about prior knowledge.  We will cover some of that material on Thursday.  In particular, we will be discussing:

* the structure of a file system
* a short overview of permissions
* how to execute a script
* Standard input, standard output, standard error, and piping
* Some relevant odds-and-ends

If these ideas are new to you (or you just want some reinforcement), then try

http://ryanstutorials.net/linuxtutorial/piping.php

**Now... back to your originally scheduled tutorial.**

Before the start of next week's lab you should complete this shell tutorial: http://www.linuxdoc.org/HOWTO/Bash-Prog-Intro-HOWTO.html. 

It may look a little daunting when you see the table of contents (there are 14 sections!), but each of the sections are very short so the reading shouldn't take long. I'd particularly concentrate on Sections 2 through 7, but the whole thing is worth reading through. I strongly would advise that you do the reading in the lab or at least at a machine that has a terminal program with the bash shell installed so you can try some of these things out.  

As you are going through the tutorial go through it once in a quick pass and don't worry too much if things don't make perfect sense the first time (this tutorial is good for review-- but frequently introduces useful information *after* the first time it uses it).  **AFTER** the first pass, if something is not making sense on your second reading, or does not seem to be working correctly **please** ask me about it.

The page http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html also has a nice set of tutorials and goes a bit deeper on some subjects (you may find it useful to read them in tandem).  However, although it's worth looking at, please don't knock yourself out trying to understand it all before next class.

In addition, the video sequence starting here:

https://www.youtube.com/watch?v=NWWvZa-qlRE (start at minute 4:34)

is quite nice.  (You'll notice that the narrator is using `nano` as their editor-- **you** should be using the editor you choose earlier.)  These videos are better about **not** assuming prior knowledge but suffer from two problems:

* It's hard to go back and find previous information
* It takes a lot longer than reading (at least for me)

Feel free to watch them.

Most Windows users won't have a version of bash, and if you're not sure you almost certainly don't. It's available standard out of box on Macs and Linux boxes; if you have a Mac, look in your Applications/Utilities and you'll fine it.  If you are using windows you can install `cygwin` (https://www.cygwin.com/).

The final thing I'll mention here is the `man` command. If during your reading or the lab you run across a command that you aren't familiar with then the man command is your friend. To find out more about a certain shell function simply type in

```man function_name_here```

This will bring up a page that (supposedly) describes what that function does. Navigate the man page with the arrow keys and press q to quit back to the command line.

Keep in mind that man pages are written by the person or persons who created the function. This means that the man pages throughout the shell vary from extremely technical and detailed to non-existent. If the man page isn't helpful, some simple googling should bring up tons of sites to supplement a poor man page.

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
