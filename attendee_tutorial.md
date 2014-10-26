---
title: Rails Girls Berlin
layout: default
---

## Attendee Tutorial

{% include attendee_app_description.md %}


{% include common_start.md %}

## 2. Create Attendee scaffold

We are using Rails' scaffolds to generate a starting point that allows us to list, add, remove, edit, and view things; in our case attendees.

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: What is a scaffold (1. the command, 2. the model name and related db table; pluralization/naming conventions, 3. attributes and types)?</span>

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: What are migrations and when do you need to do them, why?</span>


    rails generate scaffold attendee name:string twitter_handle:string bio:text address:text picture:string
    rake db:migrate
    rails s

Open [`http://localhost:3000/attendees`](http://localhost:3000/attendees) in your browser. Click around and test what you got by running these few command-line commands.

Hit **`CTRL-C`** to quit the server again when you’ve clicked around a little.


## 3. Design

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: Talk about the relationship between HTML and Rails.
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

    <div class="navbar navbar-fixed-top navbar-default">
      <div class="container">
        <a class="navbar-brand" href="/">The workshop app</a>
        <ul class="nav navbar-nav">
          <li><a href="/attendees">Attendees</a></li>
        </ul>
      </div>
    </div>

and before `</body>` add

    <footer>
      <div class="container">
        Rails Girls 2014
      </div>
    </footer>

Now let’s also change the styling. Open `app/assets/stylesheets/application.css` and at the bottom add

    body { padding-top: 100px; }
    footer { margin-top: 100px; }
    #map { width: 800px; height: 400px; margin: 30px 0; }

Now make sure you saved your files and refresh the browser to see what was changed. You can also change the HTML & CSS further.

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: Talk a little about CSS and layouts.</span>

## 4. Adding picture uploads

We need to install a piece of software to let us upload files in Rails.

Open `Gemfile` in the project directory using your text editor and under the line

    gem 'sqlite3'

add

    gem 'carrierwave'

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: Explain what libraries are and why they are useful. Describe what open source software is.</span>

In the terminal run:

    bundle

Now we can generate the code for handling uploads. In the terminal run:

    rails generate uploader Picture

At this point you need to restart the Rails server process in the terminal, as it only picks up new libraries/gems after restart.

Hit **CTRL-C** in the terminal to quit the server. Once it has stopped, you can press the up arrow to get to the last command entered, then hit enter to start the server again.

This is needed for the app to load the added library.

Open `app/models/attendee.rb` and under the line

    class Attendee < ActiveRecord::Base

add

    mount_uploader :picture, PictureUploader

Open `app/views/attendees/_form.html.erb` and change

    <%= f.text_field :picture %>

to

    <%= f.file_field :picture %>

In your browser, add a new attendee with a picture. When you upload a picture it doesn’t look nice because it only shows a path to the file, so let’s fix that.

Open `app/views/attendees/show.html.erb` and change

    <%= @attendee.picture %>

to

    <%= image_tag(@attendee.picture_url, :width => 600) if @attendee.picture.present? %>

Open `app/views/attendees/index.html.erb` and change

    <td><%= attendee.picture %></td>

to

    <td><%= image_tag(attendee.picture_url, :width => 100) if attendee.picture.present? %></td>

Now refresh your browser to see what changed.

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: Talk a little about HTML.</span>

## 5. Finetune the routes

If you try to open `http://localhost:3000` it still shows the “Welcome aboard” page. Let’s make it redirect to the attendees page.

Open config/routes.rb and after the first line add

    root :to => redirect('/attendees')

Test the change by opening the root path (that is, [`http://localhost:3000/`](http://localhost:3000/)) in your browser.

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: Talk about routes,
and include details on the order of routes and their relation to static files.</span>

## 6: Add Geolocator and Google Maps
To indicate a location on the map, we need to add another gem which will convert a human readable address into location information as used by the map itself, defined in latitude and longitude values.
Let's start by adding some code to the attendee profile which will will handle this conversion automatically for us.

Open **Gemfile** in the project and add

    gem 'geocoder'

under the line

    gem 'carrierwave'

In the **Terminal/Command Prompt** run:

    bundle

and then:

    rails generate migration AddLatitudeAndLongitudeToAttendee latitude:float longitude:float
    rake db:migrate

Open **app/models/attendee.rb** and add

    geocoded_by :address
    after_validation :geocode

after

    mount_uploader :picture, PictureUploader

We are going to include the Google Maps JavaScript API to display a map.
Open **app/views/layouts/application.html.erb** and add

    <script src="https://maps.googleapis.com/maps/api/js?v=3.exp"></script>

above

    <%= stylesheet_link_tag "application", :media => "all" %>

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: Talk a bit about the Google Maps library as well as JavaScript in general and what they can be used for.</span>

All we have to do now is to pass our list of attendees on to the Google Maps API so we can display a little red marker for each attendee on the map. Google Maps will herefor use the latitude and longitude information which has been calculated for us by the `geocoder` gem one step prior.

Add in **app/views/attendees/index.html.erb**

    <script type="text/javascript">
      function initialize() {
        var attendees    = <%= raw @attendees.to_json %>;
        var map          = new google.maps.Map(document.getElementById('map'), {
          zoom  : 4,
          center: new google.maps.LatLng(52.519242, 13.404169) // Berlin
        });
        var markerBounds = new google.maps.LatLngBounds();

        for (var i = 0, l = attendees.length; i < l; i++) {
          var position = new google.maps.LatLng(attendees[i].latitude, attendees[i].longitude);
          new google.maps.Marker({
            position: position,
            map     : map,
            title   : attendees[i].name
          });
          markerBounds.extend(position);
        }

        if (attendees.length > 0) map.setCenter(markerBounds.getCenter());
        if (attendees.length > 1) map.fitBounds(markerBounds);
      }

      google.maps.event.addDomListener(window, 'load', initialize);
    </script>

below

    <h1>Listing attendees</h1>

<span class="lead coach"><i class="icon-comment-alt">Coach</i>: Walk briefly through the JavaScript snippet and explain a bit what’s goin on.</span>

Now you need to restart the Rails server process in **Terminal/Command Prompt** by suing **CTRL + C** to shut it down and starting it again through `rails server`.
To show the attendees you've already added, you need to **update their profiles** as it has to geocode their addresses.

You might notice that the map sometimes doesn't show up if you don't reload the page. That is because of turbolinks. There are other solutions but the easiest is to just disable turbolinks:

1. Remove `gem "turbolinks"` from your Gemfile and run bundle
2. Remove `"//= require turbolinks"` from **app/assets/javascripts/application.js**.
3. Remove any `data-turbolinks-track` attributes in your **app/views/layouts/application.html.erb**.

***

## What's next?

- Add design using HTML &amp; CSS
- Add ratings
- Use CoffeeScript (or JavaScript) to add interaction
- Add picture resizing to make loading the pictures faster

## Additional Guides
Be careful,they have been created for another app, so don't forget to adapt it to this one!

* [Add commenting by Janika Liiv](http://guides.railsgirls.com/commenting/)
* [Put your app online with Heroku by Terence Lee](http://guides.railsgirls.com/heroku/)

