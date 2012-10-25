---
layout: post
title: "How to Fix a RedCloth Error While Installing Octopress"
date: 2012-10-24 15:35
comments: true
categories: 
---
[Octopress](http://octopress.org/) is a great blogging platform for coders. _(Full disclosure: This blog is run on Octopress.)_ However, when installing, sometimes strange errors come up.  A few weeks ago while setting up our blogs, my classmate [Jenya](http://innatewonderer.github.com/) ran into a strange RedCloth error while running bundle install following the [otherwise very comprehensive setup instructions](http://octopress.org/docs/setup/) provided by Octopress.  

{% codeblock lang:ruby %}
An error occured while installing RedCloth (4.2.9), and Bundler cannot continue.
Make sure that `gem install RedCloth -v '4.2.9'` succeeds before bundling.
{% endcodeblock %}

This was a little intriguing, but not hard to fix.  However, after trying to run gem install RedCloth, we got another error. 

{% codeblock lang:ruby %}
ERROR:  Error installing RedCloth:
ERROR: Failed to build gem native extension.

    /usr/bin/ruby1.9.3 extconf.rb
    /usr/lib/ruby/1.9.3/rubygems/custom_require.rb:36:in `require': cannot load such file -- mkmf (LoadError)
from /usr/lib/ruby/1.9.3/rubygems/custom_require.rb:36:in `require'
from extconf.rb:1:in `<main>'
{% endcodeblock %}

Since gem install had never failed for me when I ran it, I decided to do a little more research.  What actually is RedCloth? Why do we need it?

<!--more-->

[RedCloth](http://redcloth.org/) is a module for using the Textile markup language in Ruby. Even the official website said the gem install should work. The issue was not actually RedCloth, but it turns out after checking the mkmf.log it was an issue with gcc-4.2 also not being found.

[gcc](http://gcc.gnu.org/) is the Gnu Compiler Collection.  It includes support for multiple programming languages, as well as libraries for these languages. Even after making sure that command line tools were installed with [Xcode](https://developer.apple.com/xcode/), it still didn't find the gcc compiler. It appears that the newest version of Xcode has removed gcc in favor of [clang](http://clang.llvm.org/index.html). 

Luckily, she actually had gcc on her machine, but it wasn't installed. We only needed to run the last two lines of code. If you don't, run all five lines.

{% codeblock lang:ruby %}
$ brew update
$ brew tap homebrew/homebrew-dupes
$ brew install apple-gcc42
$ sudo ln -s /usr/bin/gcc /usr/bin/gcc-4.2
$ bundle install
{% endcodeblock %}


####Sources:
https://github.com/imathis/octopress/issues/59   
http://jfire.io/blog/2012/03/02/xcode-4-dot-3-homebrew-and-ruby/   
http://stackoverflow.com/questions/12119138/failed-to-build-gem-native-extension-when-install-redcloth-4-2-9-install-linux    
http://jgarber.lighthouseapp.com/projects/13054/tickets/215-native-ext-compilation-failure









