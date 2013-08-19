---
title: Step 3
layout: default
---

## Step 3: Design
<p class="lead coach">Coach: Talk about the relationship of HTML and Rails; what part of views is HTML and what is Embedded Ruby (ERB)? How does this relate to MVC (models and controllers control the logic of dynamically generating HTML, or views)? Explain how the app folders are ordered/classified.</p>

Design doesn’t look nice. Let’s do something about it. We’ll use __Twitter’s Bootstrap__ project to give us nicer default styles really easily.

Open `app/views/layouts/application.html.erb` and add on top of

    <%= stylesheet_link_tag "application" %>

the line

    <%= stylesheet_link_tag "http://railsgirls.com/assets/bootstrap.css" %>

and swap

    <%= yield %>

for

    <div class="container"><%= yield %></div>

Let’s also add topbar and footer to the layout and style those and the attendees table. To the `application.html.erb` under `<body>` add:

    <div class="navbar navbar-fixed-top">
        <div class="navbar-inner">
            <div class="container"><a class="brand" href="/">The workshop app</a>
                <ul class="nav">
                  <li class="active"><a href="/attendees">attendees</a></li>
                </ul>
            </div>
        </div>
    </div>

and before `</body>` add:
    
    <footer>
        <div class="container">Rails Girls 2013</div>
    </footer>

Open `app/assets/stylesheets/application.css` and add to the bottom:

    #logo { 
        font-size: 20px;
        font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
        float: left;
        padding: 10px;
    }
    body { padding-top: 100px; }
    footer { margin-top: 100px; }
    table, td, th { vertical-align: middle !important; border: none !important; }
    th { border-bottom: 1px solid #DDD !important; }
    td.picture { width: 140px; }
    td.picture img { width: 140px; }

<p class="lead coach">Coach: Talk a little about CSS and layouts.</p>
