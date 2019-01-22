---
layout: post
title:      "RestFull LA React"
date:       2019-01-22 20:09:38 +0000
permalink:  restfull_la_react
---



Are you Hungry? Are you in LA? Need help finding a restaurant? You’re in the right place! You’ve found the app that helps the restless and empty in LA to REST and be FULL in LA!

![](https://media1.tenor.com/images/d2c70e7550051236ec3d1ae0449c9976/tenor.gif?itemid=3473685)

It seems I've come full circle and revisited my very first project here at Flatiron to draw inspiration for my final project. A restaurant picker was a simple and practical idea but very fitting to compare where I started to how much I've grown as a developer. For this project I built a Ruby on Rails back end and a React front end with a reactstrap layout and styles.

The Rails back end consists of only a restaurant model and a restaurants controller and a restaurants database table for persisting the data. A list of LA restaurant data is collected from the Foursquare API utilizing the Faraday gem and stored within the database. A user may also create a new restaurant to be added to that list if they choose. Bridging the gap between the back and front end for cross domain AJAX calls was easily done using a middleware gem called rack-cors.

Drawing inspiration from my first project I created a user experience flow: "Are you in LA?"; "Are you hungry?"; "Get a random pick?"; "See a list?"; etc. I used React and Redux for displaying and modifying the restaurant data via async actions. A user can receive a random pick from the list of restaurants which is displayed in the pick container or view a list of restaurants that can be filtered by a category or by a delivery option within the restaurants container. A link to add a new restaurant will display a form for creating a new restaurant and displays the new restaurant in a show container on form submit.

![](https://i.imgur.com/2wqeZ48.jpg)

Upon completion of my first project I can remember celebrating a small victory. Though completing my final project has much more weight to it(almost at the level of the release of Windows 95), I believe that It is simply another minor step toward the overall goal of a successful web development career. I have grown so much over the course of Flatirons Full Stack Web Development program and am eager for more. I find comfort knowing that the journey will continue, and the exploration has just begun.

You can check my project out on Github below.

[Github](https://github.com/Xplor8r/rest_full_la_react)
