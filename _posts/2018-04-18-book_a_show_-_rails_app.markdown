---
layout: post
title:      "Book A Show - Rails App"
date:       2018-04-18 15:59:49 +0000
permalink:  book_a_show_-_rails_app
---


I have just completed my Rails project.  It is meant to serve as a platform for venue owners to book bands to play in their venue.  The concept is something I've thought might be practical for places that operate as a secondary concert venue, such as bars or breweries.  This could create a type of classifieds system to connect with local bands looking to play shows.

The three main models in my app are Bands, Venues, and Bookings.  A booking joins a band with a venue, along with an associated datetime attribute.  Users are not fully related to these models in a practical manner as the app stands right now.  Ideally, a User could belong to a Band, or have one Venue.  In the current revision, a User only contains a boolean attribute to indicate if they are a venue owner.  This gives them authorization to create bookings.

Check out the app in this walkthrough video:
https://youtu.be/EdCv8TNai2Q

I'll share three lessons I learned, or was reminded of through the process of writing this app.

1) Be sure to consider the difference between a class method and instance method when writing any method for your models.  It is a fairly simple concept, but be sure that is the first consideration when programming a new method.  Don't just bang out a class method without thinking twice, because it may be tricky to identify that error later on.
2) Don't let Omniauth be an afterthought to your app.  Be sure that your User model has the necessary attributes to integrate with the Omniauth login flow.  For example, I setup a simple authentication system with the bcrypt gem, and only require users to have a username and password.  I ultimately used the user's 'uid' from Google as their username in my app.  If I were to display that username anywhere, it would be rather unsightly.
3) Think twice before aliasing any model relationships.  For the sake of code asthetics, I chose to alias 'bookings' as 'shows' when they relate to bands.  I thought it would be more intuitive to call `@band.shows` .  But even in an app this small, that caused a few hiccups.  Truly consider whether its worthwhile to alias anything, as the headaches would only grow with the size of the app and additional collaborators.

You can check out the code here:
https://github.com/thurman024/book-a-show-rails-app
