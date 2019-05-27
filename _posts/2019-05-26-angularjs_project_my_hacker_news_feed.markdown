---
layout: post
title:      "AngularJS Project: My Hacker News Feed"
date:       2019-05-27 01:12:11 +0000
permalink:  angularjs_project_my_hacker_news_feed
---

Hacker News uses Google's Firebase to create API endpoints that make their public data available in near real time. Using only the AngularJS front-end framework, I pulled data from the Hacker News Firebase API. A list of well over 400 Top Stories was collected as well as a list of user comments associated with each story. I then rendered these lists with CSS styling for the user in a basic web application clone of the actual [Hacker news website](https://news.ycombinator.com/).

![](https://techcrunch.com/wp-content/uploads/2013/05/hacker-news1.jpg?w=600)

For the purpose of data collection I setup a PostsService with a `getTopStories()` function to grab all the top stories and a `getPost()` function to grab information about a single post by it's ID. In order to create separate routes for a list of stories and a list of comments for a selected story I install angular-ui-router. In the App.js file a route (or state) for the '/top' url and '/post' url are given a template url and a controller to manage the data provided from the PostsService methods.

Within the `TopStoriesController()` a `paginatePosts()` method allows only 25 top stories to be shown at a time by slicing the array of posts. A `nextPage()` method and previousPage() method are used for pagination buttons allowing users to navigate to different sections of the full list of top stories. 

An `Item` component has it's controller set to call the `getPost()` for taking data from the initial URL. It was necessary to install ngSanitize inorder to be able to inject HTML into the `views/item.html` template using `ng-bind-html="item.data.text"`. Because each individual post has a specific type property of either `story` or `comment`, I was able to use `ng-switch` directive to render each differently.

After completing this project, I was able to reach my goal of gaining a solid knowledge of the AngularJS framework. My next goal is to build an identical app using the latest version of ReactJS. I strongly believe that the ability to migrate from one framework to the next is a skill most developers overlook. However, as web and software technologies continue to rapidly advance every career developer will most likely be faced with the need to change from an old framework to the next best thing.

[View code on GitHub](https://github.com/Xplor8r/My_Hacker_News_feed)



