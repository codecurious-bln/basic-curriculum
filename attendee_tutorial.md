---
title: Rails Girls Berlin
layout: default
---

# Attendee Tutorial

{% include attendee_app_description.md %}


{% include common_start.md %}

# 2. Create Attendee scaffold

We are using Rails' scaffolds to generate a starting point that allows us to list, add, remove, edit, and view things; in our case attendees.

<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: Coach: What is a scaffold (1. the command, 2. the model name and related db table; pluralization/naming conventions, 3. attributes and types)?</span>

<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: What are migrations and when do you need to do them, why?</span>

 
    rails generate scaffold attendee name:string twitter_handle:string bio:text address:text picture:string
    rake db:migrate
    rails s
    
Open `http://localhost:3000/ideas` in your browser. Click around and test what you got by running these few command-line commands.

Hit **`CTRL-C`** to quit the server again when you’ve clicked around a little.


