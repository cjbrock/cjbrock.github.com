---
layout: post
title: "5 Easy Steps to Getting Started with Ruby Koans"
date: 2012-10-10 15:02
comments: true
categories: 
---
[Ruby Koans](http://rubykoans.com/) are a great learning tool published by Jim Weirich and Joe O'Brien.  They will expose you to both Ruby basics and testing conventions, but getting started can be a little intimidating. I've found these five tips to be really helpful. 

## 1. Download, don't web-base.
Although the web page does offer you the option to run through the Koans online, it's an abridged version and only offers 30 modules. However, if you choose to web-base your koans, be sure to bookmark where you left off, so you can pick it back up again later.  

## 2. Read the Installing Ruby section (no, really).
Even if you already have Ruby installed, walk through the Installing Ruby section of the webpage. it shows you how to get started with the Koans. To start the Koans, simply go to Terminal (or your choice of command line interface) and while in your Koans folder, type:
{% img center /images/koans/path_to_enlightenment.png 'Path to Enlightenment' 'Path to Enlightenment' %}
The error message will point you directly to the file and line number. This will bring up your first test. You don't really need to know about testing to be able to get through the Koans, you just need to understand that whenever you see a line like this: ___ you need to delete it and fill it in with something else. 



## 3. Guess.
If you know about the Koans, chances are that you have a basic Ruby knowledge base. Our first assert tells us exactly what to do, which makes guessing is pretty easy.
{% img center /images/koans/first_assert.png 'First Assert' 'First Assert' %}
Once the assert is correct, go back to terminal and run ruby path_to_enlightement.rb again, and your test should pass. 
{% img center /images/koans/first_test_passed.png 'First Test Passed' 'First Test Passed' %}

## 4. When in doubt, test in IRB. 
You can also test the code in IRB.  This will (almost) always give you the correct answer. 
{% img center /images/koans/about_nil.png 'About Nil' 'About Nil' %}
If you don't know if nil is an object, run it in IRB.
{% img center /images/koans/nil_object.png 'Is Nil an Object' 'Is Nil an Object' %}

## 5. Google.
If you're really and truly stuck and can't figure out the error message (usually about 15 minutes is a good rule of thumb when you're having trouble) try Googling Ruby Koans and Github.  Many, many, many people have completed and committed the Koans, and a lot of them have committed them. When in doubt, check out their code and try to write your own based off their solutions. Be sure to check out a couple different solutions - all solutions are definitely not created equal.
