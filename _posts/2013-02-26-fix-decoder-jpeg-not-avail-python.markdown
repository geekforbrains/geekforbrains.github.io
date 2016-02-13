---
layout: post
title: "How to fix the \"decoder jpeg not available\" error when using PIL in Python"
date: 2013-02-26
permalink: /post/how-to-fix-the-decoder-jpeg-not-available-error-when-using-pil-in-python
---

In my experience, [PIL] can be finicky if you don't have everything just right. 
I recently encountered the following error while working on [QuoteRobot][qbot].

{% highlight shell %}
IOError: decoder jpeg not available
{% endhighlight %}

Basically this means that the `libjpeg` library isn't installed. This is easy to 
fix on Linux and Mac OSX (I'm using Mountain Lion, but future versions should work).

On Mac, you can use [Homebrew] to install the libraries. Open terminal and run:

{% highlight shell %}
brew update
brew install libjpeg libpng
{% endhighlight %}

On Ubuntu, you can use the APT package manager. Open terminal and run:

{% highlight shell %}
sudo apt-get install libjpeg-dev
{% endhighlight %}

Once you've installed the libraries, you'll need to __re-install__ PIL. Run the 
following:

{% highlight shell %}
pip install -I PIL
{% endhighlight %}

Note that if you're installing PIL system wide, you'll need to prepend `sudo` to 
that command. However, I'd recommend using [Virtualenv] instead.

Hopefully this will save you some time.

[PIL]: http://www.pythonware.com/products/pil/
[qbot]: https://quoterobot.com
[Homebrew]: http://brew.sh
[Virtualenv]: https://pypi.python.org/pypi/virtualenv