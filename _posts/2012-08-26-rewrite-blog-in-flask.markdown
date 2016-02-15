---
layout: post
title: "Adventures of rewriting my blog in Flask"
date: 2012-08-26
permalink: /post/adventures-of-rewriting-my-blog-in-flask
redirect_from: /permalink/bd0058a940/
---

__NOTE:__ This post is no longer relevant. I'm now using GitHub Pages and Jekyll 
to run this site.

The last couple of days I've been thinking about something I can build as a way learn [Flask][@flask]. I started re-writing my Blog while following a tutorial, but it quickly became boring and repetitive. I needed something a little more unique.

While on a trip to Vancouver for GrowConf, I discovered [Octopress][@octopress], a static blog site generator built off of Jekyll. I fell in love. Quickly create posts in your favorite editor ([Vim][@vim]) using Markdown and push to live? Awesome!

My new Flask project? Re-create this blog by building a static site generator. My goal was to be able to write posts or pages in Markdown and have the system automatically map filenames to routes. I used [Git][@git] and [Fabric][@fabric] for deployment, and for the layout, I used [Bootstrap][@bootstrap].

One might make the argument, "Why not just use Octopress?". I totally agree, but the point was to have something to play with as a way to learn. Sure I could have used a pre-built tool, but where's the eduation (and fun) in that?

So far I'm really happy with the end product. Its nice writing in a familiar editor instead of something like TinyMCE or Redactor. Plus the whole thing is versioned and backed up thanks to my Git repo. It may not have all the bells and whistles like some of the tools out there, but it gets the job done. I plan to add more features as I need them.

If you'd like to see the source, I put it on [GitHub][@squid]. I nicknamed the project "[Squid][@squid]".

[@flask]: http://flask.pocoo.org
[@octopress]: http://octopress.org
[@vim]: http://www.vim.org
[@git]: http://git-scm.com
[@fabric]: http://fabfile.org
[@bootstrap]: http://twitter.github.com/bootstrap/
[@squid]: http://github.com/geekforbrains/squid