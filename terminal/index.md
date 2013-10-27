---
title: Rails Girls Berlin
layout: default
---

# Get to know the tools

<i class="icon-file-text icon-2x"> Text Editor</i>

<p class="lead">Sublime Text, Komodo Edit, Vim, Emacs, and Gedit are examples of text editors your can use for writing code and editing files.</p>

<i class="icon-terminal icon-2x"> Terminal (known as Command Prompt on Windows)</i>

<p class="lead">Where you talk to your computer.</p>
* Mac OS X: Open Spotlight, type Terminal and click the Terminal application.
* Windows: Click Start and look for Command Prompt, then click Command Prompt with Ruby on Rails.
* Linux (Ubuntu): Search for Terminal on the dash and click Terminal.

<i class="icon-desktop icon-2x"> Web browser</i>

<p class="lead">(Firefox, Safari, Chrome) for viewing your application.</p>

## Important

......

# 1. Get to know the terminal

We’re going to familiarize ourselves with moving around our folders without using the graphical interface

When you start the terminal the bash program starts off automatically and leaves you with the command prompt, which looks like this:

    $

When the command prompt is not visible you cannot execute new commands.
First, let’s open a terminal and type into the command prompt a command that prints your current working directory

    pwd

With ls you can get a list of all the content in that directory:

    ls

To get into one directory run cd followed by the name of a directory:

    cd documents

To get one level up again run

    cd ..

A short-cut to your home directory is the tilde:

    ~

Now navigate to the place in your folders where you want to store all RailsGirls tutorials. To create a directory named railsgirls run:

    mkdir railsgirls

Now move into that directory:

    cd railsgirls

Let's create a text file there:

    touch hello.txt

Let's type ls to see if it is there:

    ls

Let's open that file in your editor. Open your editor and in the menubar use File>>Open to open the file.
Save this text there:

    "This is some example text in my text file"

You can look at the content of your text file using cat in the terminal:

    cat hello.txt

Ok, this should be enough about files and the terminal right now. Later we get back to this, when we save code in files.    


The terminal is not only a means to talk to your computer, it can also run many programs.

# 2. Get to know the irb program


Now let's open a ruby terminal

    irb

As you notice the command prompt is gone and we have entered another program on our terminal called the ruby terminal.
Ther ruby terminal is an environment that understands and executes ruby code. You can try out all commands you did during this tutorial: 'http://tryruby.org' which is a browser based ruby environment

    
For example:

    "Hello World"

And as we know Ruby knows math too:

    1 + 5

Let's store something in a variable:

    planet = "earth"

Variable names are always written in lower caps. In our example we are storing a string into a variable. A string is not-coding text literal written in quotation marks (can be singel or double quote).

Let's output the variable

    planet
As you can see the ruby terminal gives you feedback on what you typed. We can also call it the return value.

You can also output any string:

    "earth"

Just like any number or math:

    55555

Let's overwrite our variable with another value:

    planet = "mars"

Let's output the variable again to see the different return value:

    planet

Let's open that file in your editor. Open your editor and in the menubar use File>>Open to open the file.
Save this text there:

    puts "Hello"
    puts 1+1
    a = "I am feeling good today"
    print a

You can now run this file in the terminal:

    ruby hello.txt

If you enjoyed running .rb files in the terminal, here are some more commands you can try out (save the text in the files and run it in the terminal)
http://pine.fm/LearnToProgram/?Chapter=01
up to half of chapter 5 (the line width stuff is pretty boring, all until then is fine)


