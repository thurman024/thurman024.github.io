---
layout: post
title:      "BrewTrack Sinatra App"
date:       2018-03-06 12:04:27 -0500
permalink:  brewtrack_sinatra_app
---


The programming knowledge I've accumulated over the last weeks has begun to blossom into the ability to create legitimate web apps.  For the second portfolio project, I have created a beer tracking app to store and organize beers by their associated brewery and style.

Planning out the application, everything seemed straightforward based on the material and labs from the curriculum.  I would use multiple models and relationships, similar to the Playlister lab.  For my app, a beer would be the primary model.  A beer instance would belong to a brewery and also a style. Conversely, a brewery and style would have many beers.  Although there is an indirect relationship between breweries and styles through beers, I decided that this relationship was not useful for my app.  Additionally, I would include a user model, following the pattern of the Fwitter lab.

Coding the application was equally straightforward.  My process was to create a route, then the applicable view page, then verify that it functioned as intended.  Once the foundational portion of the app was functional, I added in some seed data to aid in verifying the app's behavior.  Fully developed, the app provides full CRUD functionality for a beer, and index/show ability for a brewery or style.  A user also has a homepage showing all entries they have submitted.

The final step was to add a navigation bar with links to the main pages of the app.  This required me to reference some previous HTML/CSS material, but was very valuable in allowing my app to resemble a legitimate web app.  The final product certainly won't win any award for asthetics, but programming a fully functional app inspires me with confidence in my abilities and a growing desire to learn more!

[Watch the walkthrough](https://youtu.be/InMA1ZELtAQ)
[View github repo](https://github.com/thurman024/brewtrack-sinatra-app)
