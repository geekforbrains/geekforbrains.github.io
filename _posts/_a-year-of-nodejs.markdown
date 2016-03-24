---
layout: post
title: "After a year of using NodeJS in production"
date: 2016-03-24
permalink: /post/after-a-year-of-nodejs-in-production
---

This is a follow-up post to my original ["Why I’m switching from Python to 
Node.js"][article]. I wrote it just over a year ago in response to my
frustrations with Python and why I was going to try Node instead.

Fast-forward a year of in-house CLI tools, client projects and updates to our 
companies products and this is what I've learned.

### Easy to learn, impossible to master

Node is great for this. Especially if you already know some Javascript. Google a 
few beginner tutorials, play with Express and you're off to the races, right? 
Then you realize you'll need to settle on a database. No problem, lets search 
NPM. Oh, theres a handful of decent SQL packages. Later you realize all the ORM 
tools suck and a basic driver is your best bet. Now you're stuck implementing
redundant model and validation logic. Shortly after that, you start writing
more complex queries and start getting lost in callbacks. Naturually you read
about callback hell, chop down your christmas tree and start using one of the 
many promise libraries. 

All this to say that it feels like the Node ecosystem is constantly moving. Not
in a good way. New tools that "trump" old tools seem to come out daily. Theres
always a new shiny thing to replace your other with. You'll be surprised on how
easily this happens to you. Packages that consist of trivial code no more than 10
lines of code are downloaded in the thousands every day from NPM. Seriously!?
You need a dependancy for array type checking?

You'll never master something that moves at breakneck speed. Just waste time.

### Good luck handling errors

Coming from other languages such as Python, Ruby or PHP you'd expect throwing
and catching errors, or even returning an error from a function would be a
straightforward way of handling errors. Not so with Node. Instead, you get to
pass your errors around in your callbacks (or promises) - thats right, no 
throwing of exceptions. This works until you're more than a few callbacks deep 
and trying to follow a stack trace. Not to mention if you forget to return your
callback on an error, it continues to run and triggers another set of errors
after you returned the initial one. 

Even if you do manage to come up with a solid standard for your own errors, you
cant confirm (without reading the source) that the many of NPM packages you have
installed follow the same pattern.

These issues have lead to the use of "catchall" exception handlers that can log
an issue and allow your app to gracefully shit its pants. A+.

### Callbacks, promises or generators!?

TODO

### Bad standards

TODO

[article]: /post/why-im-switching-from-python-to-node-js
