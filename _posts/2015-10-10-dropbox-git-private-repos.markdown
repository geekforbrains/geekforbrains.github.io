---
layout: post
title: "How to use Dropbox and Git for private repos"
date: 2015-10-10
permalink: /post/how-to-use-dropbox-and-git-for-private-repos
redirect_from: /permalink/1d4d71d05d/
---

I love GitHub, especially for open source and team projects. However, sometimes I want to develop an app personally, but don’t want to release it as open source and don’t want to pay for GitHub premium. What to do?

The solution is quite simple actually. Create the base repo in your cloud drive of choice. In my case this is Dropbox. However, you could easily use Google Drive, Microsoft SkyDrive etc. All we’re doing is referencing paths on your local computer, the cloud services do the rest.

### Step 1 - Setup the base repo

Create the initial base repo wherever you want it to be stored. I keep this in Dropbox.

{% highlight shell %}
git init --bare ~/Dropbox/myrepo.git
{% endhighlight %}

### Step 2 - Add Git to your project

Now, inside the project you've been working on (or an empty project directory if you haven’t started yet), setup Git and add the initial files

{% highlight shell %}
cd ~/MyProject
git init
git add --all
git commit -m “Initial commit"
{% endhighlight %}

### Step 3 - Add your (Dropbox) remote

Inside your project, you’ll want to be able to push commits to your new Dropbox repo. To do that, we add a new remote. Still inside your projects directory from Step 2, run:

{% highlight shell %}
git remote add origin ~/Dropbox/myrepo.git
{% endhighlight %}

### Step 4 - First push

Almost finished! Make your first push. At this stage I like to set the upstream so I can just type `git push` instead of `git push origin master`.

{% highlight shell %}
git push --set-upstream origin master
{% endhighlight %}

Now as you work on the project, you can simply do:

{% highlight shell %}
git push
{% endhighlight %}

Boom! Private repos synced to the cloud and free thanks to tools such as Dropbox or Google Drive.
