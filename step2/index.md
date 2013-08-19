---
title: Step 2
layout: default
---

## Step 2 Create attendee scaffold
We are using Rails’ scaffolds to generate a starting point that allows us to list, add, remove, edit, and view things; in our case attendees.

Coach: What is a scaffold (1. the command, 2. the model name and related db table; pluralization/naming conventions, 3. attributes and types)? What are migrations and when do you need to do them, why?

    rails generate scaffold attendee name:string twitter_handle:string bio:text address:text picture:string
    rake db:migrate
    rails s

Open [http://localhost:3000/attendees](http://localhost:3000/attendees "localhost") in browser.

**CTRL-C** exits the server when you have clicked around for a little.

[ Step 3 &gt;](/step3)