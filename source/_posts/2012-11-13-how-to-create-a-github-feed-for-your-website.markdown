---
layout: post
title: "How To Create a Github Feed for Your Website"
date: 2012-11-13 14:48
comments: true
categories: 
---
{% img right /images/GithubFeed/octocat-class-act.jpg  'Octocat Rocks' 'Octocat Rocks' %}

When we were designing our [student pages](http://students.flatiron.com/corinnabrock) at the [Flatiron School](http://flatironschool.com), one of our major questions was what to include. As programmers, one of the best ways that we can get noticed is to have our open-source projects available in as many places as we can find them.  [Github](http://www.github.com) allows you to show your code to the world. The Octopress sidebar has built-in functionality of a list of your current Github repos, but wouldn't it be cooler to have public activity feed that shows which of your repos have the most current commits?

##1. Find your Github RSS key.
Github provides an RSS key to all of your public activity.  This format of your key will be:

#####https://github.com/USERNAME.atom

Replace USERNAME with your username.  For example, my public github key would be https://github.com/cjbrock.atom. If you subscribe to your own RSS feed, the key generated will be your private RSS feed. It looks something like this: https://github.com/username.private.actor.atom?token=somehextoken. Unless you would like to expose your private key to the rest of the world, please do not use this key.

<!--more-->

##2. Use a javascript/php generator to create your code.
{% img right /images/GithubFeed/Feed2JS.png  'Feed 2 JS' 'Feed 2 JS' %}
There are many javascript PHP generators that allow you to copy and paste javascript right into your site, and will abstract away the complexity of writing your own RSS generator. [FeedtoJS](http://feed2js.org/) is the original cut and paste PHP generator.  Luckily, it's open source, and you can run your own instance of Feed2PHP if you'd like to.  But for this, just insert your RSS key, and select your options that you would like.  You can specify the number of items to display and showing and hiding item descriptions, as well as many other options.  Feed2JS will generate code for you to copy and paste into your site.

A simpler version of Feed2JS is located [here](http://itde.vccs.edu/rss2js/build.php), but it is not guaranteed to stay live.  

##3. Put the code in your application. 
Feeds are best located in a column layout.  The [Students at Flatiron](http://students.flatiron.com/corinnabrock) page uses a dual column layout with a [Twitter](https://twitter.com/cjnboston) feed, but you can use CSS or SCSS to format your output however you'd like.  
{% img right /images/GithubFeed/feed-view.png  'Feed 2 JS' 'Feed 2 JS' %}