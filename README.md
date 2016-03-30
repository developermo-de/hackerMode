#Hackermo.de

This is [Abhishek Modi](https://github.com/modi95)'s TIL blog for the [Developermode Project](http://developermo.de). 

This blog features the developermode weekly posts as well as a daily post by me (Modi). These daliy blogs are going to focus on things that I found surpring on that day, rather than only on new things I learned on that day. However on most days, both of these are the same thing.

##Contributing

Hi devlopermode member :) Once you're done writing one of my weekly posts, please submit a pull request. I'll accept it as soon as I can.

###Formatting

I'm using kramdown for the posts. Please refer to one of the existing posts if you're not familiar with kramdown.

Please make sure you have these keys in your front-matter:

```
layout: post #don't change this one 
title:  "the title of your post"
date:   2016-03-26 22:48:45 #the data and time of writing
author: Abhishek Modi (hackermode) #Your full name follwed by your mode name in parens
attr: http://developermo.de #your mode url
description: "A blurb for the meta-description"
categories: #don't change this one
- weekly
```

Certain keys have comments asking for them to not be changed. Please include these keys without any changes :heart:

###Building

1. Fork and clone the repository. 
2. Create your post in ```_posts``` and give it the appropriate file name.
3. Rememeber to ```bundle install```.
4. Use ```./devtest``` to serve and test. (This just runs ```bundle exec jekyll serve --config _config-dev.yml```)

Once you're done, submit a pull request :)

