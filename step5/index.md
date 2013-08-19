---
title: Step 5
layout: default
---

## Step 5: Finetune the routes
If you try to open [http://localhost:3000/attendees](http://localhost:3000/attendees "localhost") it still shows the default page. 

Let’s make it redirect to the attendees page. Open `config/routes.rb` and add the following after the first line:

    root :to => "attendees#index"

<p class="lead coach">Coach: Talk about routes.</p>
