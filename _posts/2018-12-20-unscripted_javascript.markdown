---
layout: post
title:      "Unscripted Javascript"
date:       2018-12-20 07:19:16 +0000
permalink:  unscripted_javascript
---

As I dove into my Rails with JavaScript project, I had a great head start as was able to let things develop somewhat organically. During the past Rails project I had a solid vision for front-end possibilities and enjoyed setting up selectors for a good amount of CSS styling. Fitting each of the JSON and Ajax requirements into my existing framework was more exploration than fulfilling this school assignment. I seemed to descend into several rabbit holes, some of which I had to back out of, while others were a very rewarding.

![](https://i.gifer.com/cn2.gif)

Object Oriented JavaScript allows one to keep things organized when programming for the front-end much like the back-end. I used an ES6 class for User to construct a slug version of a user name and a Post class to aid in showing posts on the thread index and show pages. After a bit of googling, I discovered a way to render a proper date using a formating method on Date prototype. 

It got serious when I ran into some issues with my serializers. It seems that an issue working through my has_many and belongs_to relationships forced me to serialize all user data and not just the user name. I realize now that when you serialize user data you want to prevent hackers from accessing emails and password hashes. 

Creating API end points and working with Active Model Serialization and JSON was pretty straight forward. Next and Previous links rendered each thread on a show page one at a time including a corresponding form for creating a new post. When a new post is submitted, it is rendered on the page via an Ajax post request. On the thread index page a read more link allows a user to see the full body of the first post (each thread shown initially only displays a truncated first post body). Also, below the first post body, I included a comments link informing the user how many more posts(comments) are associated with each individual thread. When this link is clicked all associated posts are rendered via and Ajax get request.

![](https://thumbs.gfycat.com/ThirstyScalyGalapagosdove-small.gif)

Well, after another 12+ hour day in front of the computer, I am happy to type the words "project completed". I am so blown away by everything I have learned in the past few months. Though I seem to have built a personal method of ordered chaos while working on projects I feel each day a grow as a developer. As I begin the last leg of the school, I feel overwhelmed by the mental strength required to quickly progress through this online program. My longing to reach the light at the end of the rabbit hole drives my passion to advance to the next level.
