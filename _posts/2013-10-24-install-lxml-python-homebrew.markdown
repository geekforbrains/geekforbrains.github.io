---
layout: post
title: "How to install lxml for Python using Homebrew and PIP in 3 steps"
date: 2013-10-24
permalink: /post/how-to-install-lxml-for-python-using-homebrew-and-pip-in-3-steps
---

Installing _lxml_ can be a pain in the ass. Just running the _pip install_ 
sometimes isn’t enough, and produces a plethora of errors. Here’s how to get it 
installed.

Note that these install steps are for Mac OSX only.

### Step 1

Download and install the latest Xcode command line tools. I like to download the 
individual package right from the Apple site.

Look for the latest available release of “Command Line Tools”.

### Step 2

Install _libxml2_ using Homebrew. You can do that by running:

{% highlight shell %}
brew install libxml2
{% endhighlight %}

### Step 3

Finally, install _lxml_.

{% highlight shell %}
pip install lxml
{% endhighlight %}

I like to install into a virtual environment as to not muddy the global space. 
I recommend you do to. To learn more, check out [virtualenv].

[virtualenv]: https://virtualenv.readthedocs.org/en/latest/
