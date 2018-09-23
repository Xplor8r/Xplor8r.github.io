---
layout: post
title:      "RestFull LA CLI"
date:       2018-09-23 00:13:26 +0000
permalink:  restfull_la_cli
---


Are you Hungry? Are you in LA? Need help finding a restaurant? You're in the right place! You've found the app that helps the restless and empty in LA to rest and be full in LA!

![](https://media1.tenor.com/images/d2c70e7550051236ec3d1ae0449c9976/tenor.gif?itemid=3473685)

Beginning with an idea is how any great creation begins. Well, it seemed like my first portfolio project began with the idea of the name. A restaurant picker was the obvious choice for helping the user to rest and be full. Since I'm currently living in the LA area, I wanted to focus on providing a selection of local restaurants. Scraping critics pick restaurant information from [***www.laweekly.com/restaurants/guide***](https://www.laweekly.com/restaurants/guide) was a great choice for me to bring my App to life.

![](https://media1.tenor.com/images/c0c2264911d8cd4a688acd0542240f95/tenor.gif?itemid=7603564)

Sometimes I feel like a clueless baboon when I'm coding. I seem to push myself through that feeling and realize that I'm actually a highly intelligent Homo sapien. Alot of times it seems like the first few minutes to an hour I get a bit of coders block. That was definitely the case for this project.

Once I had my gem set up for my project, I was able to hit the ground running and get coding. I began to build my cli and decided to add in alot of interactivity. I also wanted my app to be very easy to use, so I went with a simple yes or no question format. Once I created all of my basic methods, I stubbed out the information that I wanted to provide and did a test run. It worked! I did alot of clean up and would come back to my cli alot to make sure everything clicked well for the user.

Next, I worked on scraping. The LA Weekly restaurant guide was reasonably easy to scrape. I did run into one snag, though. One of the list items was an inline advertisement! I had to account for this with a conditional. No big deal. That's a great thing to remember. Ads are everywhere on sites and if you scrape a site you have to check that every single css selector is exactly what you're looking for.

Lastly, I created my restaurant object in order to store my restaurants and their information. Each instance of a restaurant would carry a name, a location, cuisine types and a link to more info about the restaurant. By the time I reached this point in the project, I could see potential for my app to really be something useful.

![](https://media.giphy.com/media/HTeC2galm8oj6/giphy.gif)

Celebrating a small victory is crucial for learning, especially if it is your first. It is clear to me that I could spend months on my App to bring it to its full potential and still want more. Yet, as a brand-new developer I can easily say that completing my first real functioning creation will always be a very significant achievement.


