---
layout: post
title:      "Snow-report CLI Data Gem"
date:       2018-02-08 04:46:54 +0000
permalink:  snow-report_cli_data_gem
---


My first portfolio project is on the books.  It is a CLI data scraping gem that allows a user to interact with snow condition data scraped from 'onthesnow.com'.  If I can clear one last hurdle, it will be available on Rubygems.org.

Getting started was certainly the most intimidating step of this project.  It felt like standing at the top of a double black diamond.  After some reading and watching the provided walkthrough video, I began by creating a gem through bundler.  This automatically set up the framework for the whole project, so that first step gave me the confidence to plunge ahead.

I followed the process layed out in the walkthrough video.  Starting with the user interface, I developed the CLI class first, using hard-coded responses to ensure the program would navigate properly based on user input.  Next, I coded the class responsible for instantiating objects, using pseudo data to test "real" output from the CLI.  Next, I got to work on the final class, which would be responsible for scraping data from the website.  Using the trial and error methods learned from the scraping labs, the scraper was eventually able to collect the data needed for my program.

Having worked front to back, I now needed to reverse this approach by refining my program to operate with real data.  This step mainly consisted of tweaking my methods to properly sort data.  I also spent many iterations testing functionality to find and debug any flaws in the CLI control flow (which gives me a fuller appreciation of test suites).

The fully functional program will create an object for each ski resort scraped. Each object has attributes of state, snowfall past 72 hours, base snow depth, number of runs open, and finally a link to a full ski report.  The CLI allows the user to sort the data by any of the first four attributes.  Typing the name of a resort will print all data for that resort.  After printing the requested data, the CLI will accept another command repeatedly until the user types 'exit'.
