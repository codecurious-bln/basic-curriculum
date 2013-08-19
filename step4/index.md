---
title: Step 4
layout: default
---

## Step 4: Adding picture uploads
We need to install additional library to add image processing. Open `Gemfile` in the project and add

    gem 'carrierwave'

under the line

    gem 'sqlite3'

<p class="lead coach">Coach: Tell what libraries are and why they are used. Maybe few words about Open Source?</p>

Now we generate the needed code for picture handling.

In the **Terminal/Command Prompt** run:

    bundle

At this point you need to restart the Rails server process in Terminal/Command Prompt. This is needed for the app to load the added gem.
Then you can start adding the picture upload by running a command:

    rails generate uploader Picture

Open `app/models/attendee.rb` and add

    mount_uploader :picture, PictureUploader

under the line
  
    class Attendee < ActiveRecord::Base

Open `app/views/attendees/_form.html.erb` and change

    <%= f.text_field :picture %>

to

    <%= f.file_field :picture %>

and

    <%= form_for(@attendee) do |f| %>

to

    <%= form_for(@attendee, :html => {:multipart => true}) do |f| %>

The view doesn’t look nice, it only shows a path to the file, so let’s fix it. Open `app/views/attendees/show.html.erb` and change

    <%= @attendee.picture %>

to

    <%= image_tag(@attendee.picture_url, :width => 600) if @attendee.picture.present? %>

<p class="lead coach">Coach: Talk a little about HTML.</p>