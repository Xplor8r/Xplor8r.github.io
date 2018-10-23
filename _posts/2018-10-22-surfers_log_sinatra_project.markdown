---
layout: post
title:      "Surfers Log Sinatra Project"
date:       2018-10-22 23:26:58 -0400
permalink:  surfers_log_sinatra_project
---



### Surf, log, share, using a new app called Surfers Log. Recording your surf sessions allows you to relive those epic days and to dial in a specific spot with specific conditions. Sign up today and start logging!

![](https://surfheatercom.files.wordpress.com/2017/01/sportofkings.gif?w=376)

Because I am passionate about surfing, I chose to create a surfing social network where surfers can share their surfing experiences. I quite enjoyed myself working on this project. Well, at least by half way through I began enjoying myself. Apparently, there is a minimum of one major hurdle that stands in my way during any project I pursue. I found myself stuck in the mud shortly after commencing. Setting up my Gemfile required getting through alot of unfamiliar errors involving my ActiveRecord version and my usage of Rack Flash.

Once I cleared up some bugs, I quickly set up an App folder structure to organize my Models, Views and Controllers. A public folder holds CSS, Javascript, and image folders. I also included a Readme file and last but not least a config folder with an environment file to get things moving.

The overly common model name of user is so, shall we say, used. I chose to set up a Surfer model which has many log_entries and a LogEntry model that belongs_to a surfer. Via rake:migrate commands in the terminal I set up a database table for both models. There is an application_controller and each model has their own controller. The Log_entries_controller handles the CRUD routes while the surfers_controller handles routes for login and sign up and validates a surfers password. 

![](https://media.giphy.com/media/xT0GqJfdLcrcpSbZf2/giphy.gif)

From this point the possibilities were endless. Bootstraps framework became a close friend to me and helped me streamline the front end process. Images, a nav bar, forms, CSS stylesheets and JavaScript all came together into a nice box that looks clean and feels great to use. Please feel free to check it out!

* [Surfers Log Video Demo](https://youtu.be/PpkXoG4JFLY)

* [Surfers Log Github Repo](https://github.com/Xplor8r/surfers-log)


