---
layout: post
title: "Testing in Ruby with RSpec"
date: 2012-10-16 08:58
comments: true
categories: 
---
Why do we test in Ruby? Ruby is a test-driven development language.  Testing inherently shows you where your application should go next. It allows you to specify the behavior that you think should happen (and isn't currently) before you write code to enact that behavior.  There are many methods of testing in Ruby and Rails, but the one gaining the most popularity is [RSpec](http://rspec.info/). 

RSpec is a behaviour-driven development tool for Ruby programmers. Behavior-driven development is an approach to software development that combines test-driven development, domain driven design, and acceptance test-driven planning. RSpec includes a command line program, text descriptions of examples and groups, customized reporting, expectation language, and built-in mocking/stubbing framework.

As a beginner, I'm already thinking:
#Ok. What?

{% img left /images/RSpec/trafficlight.png 'Red Green Refactor' 'Red Green Refactor' %}
##Red-Green-Refactor
If you've completed the [Ruby Koans](http://rubykoans.com/), you've already been exposed to testing syntax.  Testing in Ruby is done by a Red-Green-Refactor method. 

- talk about red-greeen-refactor
- talk about writing only what you need
- go through some simple syntax
- matchers
- dos and don'ts
