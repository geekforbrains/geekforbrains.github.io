---
layout: post
title: "Merging Local & Server Collections In Meteor JS"
date: 2015-06-23
permalink: /post/merging-local-server-collections-in-meteor-js
redirect_from: /permalink/e77252dde8/
---

Up to this point, you’ve been working with Meteor and its collections with ease. Publish here, subscribe there. Then it happens. The app you’re working on has a combination of local (client) and server related collection data that needs to be displayed in a merged list within your template. Now what?

The real world example of this happened to me a few days ago. I was working on a simple chat tool within a client project. The chat would have a “bot” that responds to keywords inline like any other message. The problem is, I didnt want to send those bot “messages” to the global message collection when only the local user would be consuming them. My goal was to combine the messages of all users as well as local messages of the bot into a single collection that could be displayed in the chat window.

*Note that the following examples assume you know how to publish Meteor collections and put the right code in their specific client or server areas.*

## The Wrong Way

You might be thinking the “right way” to do this is to fetch both sets of documents and merge the arrays using Underscore.js’ sortBy function.

{% highlight javascript %}
Local = new Mongo.Collection(null); // Local, client only
Items = new Mongo.Collection('items'); // Global, everywhere

Meteor.publish('items', function() {
  return Items.find();
}

Template.listItems.helpers({
  items: function() {
    var local = Local.find().fetch();
    var items = Items.find().fetch();
    var combined = local.concat(items);
    return _.sortBy(combined, function(i) {return i.timestamp});
  }
});
{% endhighlight %}

You’d be wrong. There are a couple issues with this approach:

#### Wasteful Queries

The first issue is every time either collection changes, both need to be re-fetched and combined. Depending on the size of your array and number of changes happening, this can be very intensive.

#### Limited Filtering

While you can sort by the timestamp ascending, what happens when you need a more complex sort? You could of course add that logic to the helper, which will now also be re-run every time either local or global collection changes. Are your hacker-senses tingling? They should be!

## The Right Way

The best way to manage these two result sets is to combine them into a single collection that can be queried and filtered as needed.

{% highlight javascript %}
Local = new Mongo.Collection(null); // Local, client only
Items = new Mongo.Collection(‘items’); // Global, everywhere

Meteor.publish('items', function() {
  return Items.find();
}

Template.listItems.onCreated(function() {
  Meteor.subscribe(‘items’);
  Items.find().observe({
    added: function(item) {
      Local.insert(item);
    }
  });
});

Template.listItems.helpers({
  items: function() {
    return Local.find();
  }
});
{% endhighlight %}

The key difference here is the use of the .observe function. Every time a new global item is added, we insert it into the local. We then return the cursor for the local collection and work with it like any other collection.

The real beauty is in the ability to filter at will. First, we can filter the global subscription and query in the templates onCreated callback. This way we can really drill down to only the data we need. Second, we have the full sorting and querying ability of a collection right on our client.