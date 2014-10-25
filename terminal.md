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


# 1. Get to know the terminal

We’re going to familiarize ourselves with moving around our folders without using the graphical interface

When you start the terminal the `bash` program starts off automatically and leaves you with the `command prompt`, which looks like this:  `$`.

When the command prompt is not visible you cannot execute new commands.
Let's start with a command that prints your current working directory

    pwd

With ls you can get a list of all the content in that directory:

    ls

To get into one directory run cd followed by the name of that directory:

    cd documents

To get one level up again run

    cd ..

A short-cut to your home directory is the tilde: `~`

<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: You can talk about auot-completion with the tab command</span>

Now navigate to the place in your folders where you want to store all Rails Girls tutorial materials and exercises. To create a directory named "railsgirls" for example run:

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
Ther ruby terminal is an environment that understands and executes ruby code. You can try out all commands you did during this tutorial: `http://tryruby.org` which is a browser based ruby environment.

You can quite `irb` anytime by typing `exit`.

## Strings and Integers
    
For example you could write this and hit Enter:

    "Hello World"
Any word literals that are not numbers or code need to be written in quotation marks ("" or '') so ruby terminal knows what it is.

And as we know Ruby knows math too:

    1 + 5
Ruby knows integers, no need to mark them specifically.

## Variables

Let's store something in a variable:

    planet = "earth"

Variable names are always written in lower caps. .

Let's output the variable

    planet
As you can see the ruby terminal gives you feedback on what you typed. We can also call it the return value.

You can also output any string:

    "earth"

Just like any number or math:

    55555

Overwrite our variable with another value:

    planet = "mars"

Greet the planet using a string and a variable:

    puts "Hello" + planet

Add an empty space:

    puts "Hello " + planet

Add an exclamation mark:

    puts "Hello " + planet + "!"

Capitalize the planet:

    puts "Hello " + planet.upcase + "!"

##Arrays

An array is way how one can store a list or a collection in a certain format. Let's create a list of planets stored in an array. You can imagine it like a bookshelf.

Creating an empty array:
    planets = []

Now we add our variable to that array
    planets.push planet

Let's add some more planets directly (hit enter after each line)
    planets.push "earth"
    planets.push "saturn"
    planets.push "jupiter"

Let's just print out our array
    planets 

Look at the size of it:
    planets.size

You can also print the first one:
    planets.first
is the same as
    planets.[0]
You should know that an array starts counting with 0. So the last one would be `planets.[3]`

##Iteration
Iteration means looping through an array and doing something with each item. Looping means you repeat the same action over and over until an halt. In our example we will perform the same action on the first item in the array to the last one. The placeholder for those items is stored in the pipes | |.

Now we are just saying `puts` to each of the items:
    planets.each do 
      |x| puts + x 
    end

Now we add `upcase` :
    planets.each do 
      |x| puts + x.upcase 
    end

Now we add an `"Hello "` to it:

    planets.each do 
      |x| puts "Hello " + x 
    end

<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: If students get stuck probably best to exit irb and start over again.</span>

#Saving code in files
As you noticed, anytime you quit `irb` and go back in again, nothing was saved and you have to start all over again. In the long run you will want to save code in files.

So let's create a file for saving ruby code:
    touch blabla.rb


Let's open that file in your editor. Open your editor and in the menubar use File>>Open to open the file.
Save this text there:

    puts "Hello"
    puts 1+1
    a = "I am feeling good today"
    print a

You can now run this file in the terminal:
    ruby blabla.rb


If you enjoyed running .rb files in the terminal, here are some more commands you can try out (save the text in the files and run it in the terminal) [Chris Pine LearnToProgram](http://pine.fm/LearnToProgram/?Chapter=01) tutorial, you can skip any parts that are not that interesting to you, e.g. line-widths in a poem or how old you are in seconds.


<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: placeholder </span>
