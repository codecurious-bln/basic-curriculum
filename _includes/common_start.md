# Get to know the tools

Every developer has a bunch of tools to build something awesome! Get to know them to be most efficient!

<i class="icon-file-text icon-2x"> Text Editor</i>

Sublime Text, Komodo Edit, Vim, Emacs, and Gedit are examples of text editors your can use for writing code and editing files.

<i class="icon-terminal icon-2x"> Terminal (known as Command Prompt on Windows)</i>

Where you start the rails server and run commands.

<i class="icon-desktop icon-2x"> Web browser</i>

Firefox, Safari, Chrome for viewing your application.

## Important

It is important that you select the instructions specific to your operating system - the commands you need to run on a Windows computer are slightly different to Mac or Linux. 
If you’re having trouble check the Operating System switcher at the bottom of the commands.

# 1. Creating the application

We’re going to create a new Rails app called railsgirls.

First, let’s open a terminal:

* Mac OS X: Open Spotlight, type Terminal and click the Terminal application.
* Windows: Click Start and look for Command Prompt, then click Command Prompt with Ruby on Rails.
* Linux (Ubuntu): Search for Terminal on the dash and click Terminal.

Next, type these commands in the terminal:

    mkdir projects

You can verify that a directory named projects was created by running the list command: `ls`. You should see the projects directory in the output. Now you want to change the directory you are currently in to the projects folder by running:

    cd projects

You can verify you are now in an empty directory or folder by again running the `ls` command.
 
This is a good time to check your rails version, on the command line type:
 
    rails --version

Any version greater than 4 is fine (this tutorial is for rails version 4+). 
 
Now you want to create a new app called railsgirls by running:

    rails new railsgirls

This will create a new app in the folder railsgirls, so we again want to change the directory to be inside of our rails app by running:

    cd railsgirls

If you run `ls` inside of the directory you should see folders such as `app` and `config`. You can then start the rails server by running:

    rails server

Open [`http://localhost:3000`](http://localhost:3000) in your browser. You should see “Welcome aboard” page, which means that the generation of your new app worked correctly.

Notice in this window the command prompt is not visible because you are now in the Rails server, the command prompt looks like this:

    $

When the command prompt is not visible you cannot execute new commands. If you try running `cd` or another command it will not work. To return to the normal command prompt:

Hit `CTRL-C` in the terminal to quit the server.

<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: Explain what each command does. What was generated? What does the server do?</span>