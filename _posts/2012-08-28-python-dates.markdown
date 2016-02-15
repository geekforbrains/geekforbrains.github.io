---
layout: post
title: "Getting to grips with Python dates"
date: 2012-08-28
permalink: /post/getting-to-grips-with-python-dates
redirect_from: /permalink/94e6847967/
---

I don't know if its because I picked up PHP first, but learning to work with 
dates in Python has been an uphill battle. Something as trivial as converting a 
string to a date object can seem convoluted if you don't know where to start. 
I wrote this post in an attempt to address some of these common questions.

### Convert A String To A Datetime Object

This one is pretty easy, but I still see it asked all over the place. You want 
to convert a string such as `2012-04-25` to a datetime object. Here's how its 
done:

{% highlight python %}
from datetime import date time

my_date_string = '2012-04-25'
my_date_object = datetime.strptime(my_date_string, '%Y-%m-%d')
{% endhighlight %}

The meat and potatos of this is the [strptime][@strptime] function. The first 
argument is the string, and the second is the format that string is in. The 
function uses that format to parse your string and create the date object. Simple.

### Convert A Datetime Object To A Formatted String

This is basically the opposite of the previous example. You want to take a 
datetime object, say from a document record returned by MongoDB, and output it 
as a nicely formatted string.

{% highlight python %}
from datetime import date time

my_date_object = datetime.utcnow()
my_date_string = my_date_object.strftime('%Y-%m-%d')
{% endhighlight %}

The above example will get the current UTC date as a datetime object, then use 
that objects [strftime][@strftime] method to return a string in the format 
specified. You can find information on the supported [format codes][@formatcodes] 
in the Python docs.

### Convert A Datetime Object To A Unix Timestamp

Converting a datetime object to a Unix timestamp is a common step when working 
with localized dates or when making a public API where you want a standard date 
format supported by many other languages. Here's how to do it.

{% highlight python %}
import time
from datetime import date time

my_date_object = datetime.utcnow()
unix_timestamp = time.mktime(my_date_object.timetuple())
{% endhighlight %}

Here we're using the datetime objects [timetuple][@timetuple] method to create 
the argument list required by the [mktime][@mktime] function. The result is our 
datetime object as a Unix timestamp. Bam!

UPDATE:

Here’s an alternate method, thanks to Gregs tip in the comments below:

{% highlight python %}
from datetime import datetime

my_date_object = datetime.utcnow()
unix_timestamp = my_date_object.strftime('%s')
{% endhighlight %}

Both methods produce the same result, so use whichever you think looks better ;)

### Convert A Unix Timestamp To A Datetime Object

Naturally, the question after reading the above example would be: "How do I 
convert a Unix timestamp back to a Datetime object?".

Thats as easy as pie, check it out:

{% highlight python %}
from datetime import date time

my_date_object = datetime.fromtimestamp(unix_timestamp)
{% endhighlight %}

Borrowing the unix_timestamp variable from the previous example, we're simply 
passing it as an argument to the [fromtimestamp][@fromtimestamp] function. The 
result is our Unix timestamp converted back to a Python datetime object. Hooray!

### Adding "st", "nd" and "rd" to Formatted Dates

This was a question that had me scratching my head for a while. Something that 
was so easy for me in PHP, wasn't possible with the default format codes in 
Python. Luckly, I came across a simple function that produces the same result. 
It's not as clean as using a format code, but it gets the job done.

{% highlight python %}
from datetime import datetime as dt

def suffix(d):
    return 'th' if 11<=d<=13 else {1:'st',2:'nd',3:'rd'}.get(d%10, 'th')

def custom_strftime(format, t):
    return t.strftime(format).replace('{S}', str(t.day) + suffix(t.day))

print custom_strftime('%B {S}, %Y', dt.now())
{% endhighlight %}

This snippet was taken from an example on [Stackoverflow][@stackoverflow]. I’d 
recommend checking it out to see some of the other approaches and usage details.

[@strptime]: http://docs.python.org/library/datetime.html#datetime.datetime.strptime
[@strftime]: http://docs.python.org/library/datetime.html#datetime.datetime.strftime
[@formatcodes]: http://docs.python.org/library/datetime.html#strftime-and-strptime-behavior
[@timetuple]: http://docs.python.org/library/datetime.html#datetime.date.timetuple
[@mktime]: http://docs.python.org/library/time.html#time.mktime
[@fromtimestamp]: http://docs.python.org/library/datetime.html#datetime.date.fromtimestamp
[@stackoverflow]: http://stackoverflow.com/a/5891598
