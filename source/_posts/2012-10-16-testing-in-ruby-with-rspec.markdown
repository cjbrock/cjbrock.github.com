---
layout: post
title: "Testing in Ruby with RSpec"
date: 2012-10-16 08:58
comments: true
categories: 
---
_tl:dr - Testing is awesome. Do it a lot._

{% img right /images/RSpec/rubytesting.png 'Red Green Refactor' 'Red Green Refactor' %}
Why do we test in Ruby? Ruby is a test-driven development language.  Testing inherently shows you where your application should go next. It allows you to specify the behavior that you think should happen before you write code to enact that behavior.  One of the most popular methods of testing in Ruby and Rails is [RSpec](http://rspec.info/). 

RSpec is a behavior-driven development tool for Ruby programmers. Behavior-driven development is an approach to software development that combines test-driven development, domain driven design, and acceptance test-driven planning. RSpec includes a command line program, text descriptions of examples and groups, customized reporting, expectation language, and built-in mocking/stubbing framework.

As a beginner, I'm already thinking:
#Ok. What?

{% img left /images/RSpec/traffic.png 'Red Green Refactor' 'Red Green Refactor' %}
##Red-Green-Refactor
If you've completed the [Ruby Koans](http://cjbrock.github.com/blog/2012/10/10/5-easy-steps-to-getting-started-with-ruby-koans/), you've already been exposed to testing syntax.  Testing in Ruby is done by a [Red-Green-Refactor](http://redgreenrefactor.eu/) method. Basically, when you run your testing development tool, if the answer turns out red, your test fails. If it turns green, your test passes. And if it's blue, you should check out your code for a way to refactor it and make it more efficient.
###[YAGNI](http://en.wikipedia.org/wiki/You_ain't_gonna_need_it)
When you're writing an application, [feature creep](http://searchcio.techtarget.com/definition/feature-creep) is bound to happen. If you can manage to stick to a test-driven method of development, you can keep feature creep to a minimum. It would be nice to immediately scale your website for a billion users, but YAGNI: You ain't gonna need it. 

##Dos and Don'ts of Testing
Testing is actually very simple.  There are a few things to keep in mind, but overall if you trust your tests and allow them to guide your development you will not go wrong.

###Dos:
- *Write your tests first*  
The point of testing is to write the tests first, then write the code.  If you're writing tests for code that you already think works, that's not test driven development.
- *Use contexts*  
[Contexts](http://net.tutsplus.com/tutorials/ruby/ruby-for-newbies-testing-with-rspec/) allow you to show the different behaviors of your application. They should simulate real-life situations. 
- *Use shared example groups*  
[Shared example groups](http://blog.davidchelimsky.net/2010/11/07/specifying-mixins-with-shared-example-groups-in-rspec-2/) allow you to define a method, and then call that method when testing. 
- *Test your edge cases*  
It's nice if your code works for the main bulk of your cases, but you must test your edge cases. 

###Don'ts:
- *Test the framework*  
The framework works. Rails was tested as it was developed. There's no point in wasting your time testing a framework that works. 
- *Test the implementation*  
Again, the implementation works. Don't waste your time.
- *Get too clever*  
Yes, you must use contexts and edge cases, but don't drive yourself crazy trying to test every single possible outcome. We all know where the logical stopping point is - acknowledge and accept it.


_(Note: This blog post is a brief summarization of the testing techniques laid out by user Duien on [Speakerdeck](https://speakerdeck.com/u/duien/p/testing-ruby). Additional research and extrapolation is my own.)_

