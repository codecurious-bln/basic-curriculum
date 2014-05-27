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


# 3. Design

<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: Talk about the relationship between HTML and Rails.
What part of views is HTML and what is Embedded Ruby (ERB)? What is MVC and how does this relate to it? 
(Models and controllers are responsible for generating the HTML views.)</span>

The app doesn't look very nice yet. Let’s do something about that. We’ll use the Twitter Bootstrap project to give us nicer styling really easily.

Open `app/views/layouts/application.html.erb` in your text editor and above the line

    <%= stylesheet_link_tag "application", media: "all", "data-turbolinks-track" => true %>

add

    <link rel="stylesheet" href="http://railsgirls.com/assets/bootstrap.css">

and replace

    <%= yield %>

with

    <div class="container">
      <%= yield %>
    </div>

Let’s also add a navigation bar and footer to the layout. In the same file, under `<body>` add

    <div class="navbar navbar-fixed-top">
      <div class="navbar-inner">
        <div class="container">
          <a class="brand" href="/">The workshop app</a>
          <ul class="nav">
            <li class="active"><a href="/attendees">Attendees</a></li>
          </ul>
        </div>
      </div>
    </div>

and before `</body>` add

    <footer>
      <div class="container">
        Rails Girls 2014
      </div>
    </footer>

Now let’s also change the styling of the ideas table. Open `app/assets/stylesheets/application.css` and at the bottom add

    body { padding-top: 100px; }
    footer { margin-top: 100px; }
    table, td, th { vertical-align: middle !important; border: none !important; }
    th { border-bottom: 1px solid #DDD !important; }
    #map { width: 800px; height: 400px; margin: 30px; }

Now make sure you saved your files and refresh the browser to see what was changed. You can also change the HTML & CSS further.

<span class="lead coach"><i class="icon-comment-alt"> Coach</i>: Talk a little about CSS and layouts.</span>


