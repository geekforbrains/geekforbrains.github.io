---
layout: post
title: "Why I’m switching from Python to Node.js"
date: 2015-01-02
permalink: /post/why-im-switching-from-python-to-node-js 
---

Old news right? Who isn’t switching to Node these days? It seems like the new kid on the block is converting devs by the masses. I’m one of them, and here’s why.

### Python 2, or is it 3?

The lack of focus and movement between Python versions is a massive pain the ass. Yes, I know lots of libraries are being converted or have been already. However, the lack of focus and clear direction of one over the other has my confidence in it at an all time low. I know this has more to do with the community not wanting to move, than the devs, but community is what drives a project.

### Unicode Support

Have you ever tried working with Unicode in Python? Holy shit its painful. Yes there are lots of docs on the subject, but it shouldn’t be that convoluted. Python 3 is a move in the right direction, however. I’m not saying Node or Javascript are the gems in this category, but they definitely have better options.

### Circular Imports

Circular imports are the bane of any Python programmer and in my opinion are a very poor architectural choice for the language. I realize for the most part, circular imports are a sign your module design is broken. However, if you’re an experienced developer, you’ll likely spend more time shoehorning Python into your advanced patterns than anything else. Good luck with that. Node.js allows me import modules wherever the hell I want.

Side note: apparently Go has this limitation too. That makes me sad :(

### NPM vs PIP

Python has PIP, which is great. However, I frequently find more up-to-date and modern modules on NPM. With the ease of sharing on NPM comes the crap too, so you need to watch out for that. I always thought sharing on PIP was annoying, but found NPM to be easy peasy. I shared my first module in all of 5 minutes.

### Efficiency = more beer money!

Theres no doubt about it. Node is leaner than Python when it comes to hardware (if written properly). Being able to actually utilize lower end hardware and produce acceptable results is a major plus. A lot of that comes down to Nodes async nature. Yes I’m aware of Twisted and similar libraries. Have you ever actually written an async app in one of those? When building a product, speed of development is important but so is keeping overhead low. We can run the same Node project on half the hardware Python required.

### Team Familiarity

This one is always up for debate, but I like the fact the entire team usually knows Javascript at a basic level. This means they can look over Node code and get an understanding of whats going on. If they're a front-end dev, that means hooking up to API endpoints or handling views is a lot easier. Which also means less interruptions for me to help them. Yay!

### MongoDB and JSON

We love MongoDB and JSON. Node uses these two without even thinking about it. Obviously this can be done with other languages, but the ease of it is just so damn appealing I had to mention it.

### Its just Javascript

If you love Javascript like I do, this is a plus. If you hate it, not so much. I think Javascript is fun because its so expressive. There are so many ways to do something, which is great for applying specific strategies to key problems. I suppose this also spawns stupid debates like “adding semicolons vs no semicolons”. For the record, I’m pro semicolons.

### Conclusion

To be clear, I still love Python. Its been good to me over the years and I’ve written several production apps (see [Postach.io][postachio] and [QuoteRobot][qbot]) in it and regularly use it for quick server scripts. Node.js wasn’t actually my first choice, but I wanted something modern and designed for the new web. PHP, Python and Ruby are definitely not it. My first choice was to learn Go (golang) but time restrictions and the team skill-set didn’t line up with that route. A startups gotta hustle you know! Node was a happy medium that we could get hacking on right away.

What are your thoughts on modern day languages? Do you still prefer Python or others? Why? Any Node “gotchas” you can share?

[postachio]: http://postach.io
[qbot]: https://quoterobot.com