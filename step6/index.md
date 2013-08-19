---
title: Step 6
layout: default
---

## Step 6: Add Geolocator and Google Maps

To pin your location on the map, we need to add two gems: one to calculate your position, one to display it on the map. 

Let's start with implementing the geolocation to the attendee profile.

Open Gemfile in the project and add

    gem 'geocoder'

and
    
    gem 'gmaps4rails'

under the line

    gem 'carrierwave'

In the **Terminal/Command Prompt** run:

    bundle

and then:

    rails generate migration AddLatitudeAndLongitudeToAttendee latitude:float longitude:float
    rake db:migrate

Open `app/models/attendee.rb` and add

    geocoded_by :address
    after_validation :geocode

after

    mount_uploader :picture, PictureUploader

It's not finished yet, you still need to add the map to pin your location. In the Terminal/Command Prompt run

    rails generate gmaps4rails:install

Go back to `app/models/attendee.rb` and add

    acts_as_gmappable :process_geocoding => false

after

    after_validation :geocode

Open `app/controllers/attendees_controller.rb` and add

    @pins = @attendees.to_gmaps4rails

in the index method, after

    @attendees = Attendee.all

Two more step and you can see the map on the app.
Open `app/views/layouts/application_layout.html.erb` and add

    <%= stylesheet_link_tag 'gmaps4rails' %>

on a new line, somewhere between

    <head>

and

    </head>

Open app/views/attendees/index.html.erb and add

    <br/> 
    <%= gmaps4rails(@pins) %> 
    <%= yield :scripts %>

after the table.

Now you need to restart the Rails server process in Terminal/Command Prompt. To pin the attendees you've already added, you need to update their profiles.