---
layout: post
title: "Setting the default encoding in Python"
date: 2012-11-12
permalink: /post/setting-the-default-encoding-in-python
---

I recently had to force the default encoding for one of our apps, [QuoteRobot][qbot] 
(Check it out if you write proposals, quotes or invoices). You can check the 
default encoding by opening the Python terminal and running:

{% highlight python %}
import sys
sys.getdefaultencoding()
{% endhighlight %}

My output is `ascii`. This can cause issues when working with strings containing 
weird ascii and unicode characters. Now you could use the `unicode` method, but 
I found it easier to set encoding for the entire program. Especially if its a 
large app.

Here's how to do it. At the beginning of your main Python file, add the 
following:

{% highlight python %}
import sys
reload(sys)
sys.setdefaultencoding('utf-8')
{% endhighlight %}

You need the `reload` method so `setdefaultencoding` is found, otherwise you'll 
get:

{% highlight shell %}
AttributeError: 'module' object has no attribute 'setdefaultencoding'
{% endhighlight %}

Thats it. Cheers.

[qbot]: https://quoterbot.com