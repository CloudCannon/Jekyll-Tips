---
title: Search
heading: Search in Jekyll
--- 

Full-text searching is possible with Jekyll. We’ll demonstrate a number of techniques, each with their own pros and cons. In these examples we'll be searching blog posts but it could easily be a Collection or Data File.

### Client Side Search

Client side search is a good technique because it's fast for small data sets, you don't need to use a third party and you have complete control of how the results are displayed and what data is searched. However, this method is very slow on large data sets.

We'll look at an implementation using [lunr.js](http://lunrjs.com/) which is a full-text search engine. Lunr.js performs search client side so we need to populate the data using JSON.

We need to get our data in JSON format. Create `/search_data.json` with the following content:

{% highlight liquid %}
{% raw %}
---
layout: null
---
{
  {% for post in site.posts %}

    "{{ post.url | slugify }}": {
      "title": "{{ post.title | xml_escape }}",
      "url": " {{ post.url | xml_escape }}",
      "author": "{{ post.author | xml_escape }}",
      "category": "{{ post.category | xml_escape }}"
    }
    {% unless forloop.last %},{% endunless %}
  {% endfor %}
}
{% endraw %}
{% endhighlight %}

Notice how I output author and category. You may not have these properties, you can delete those lines or changes them to other properties you want to search on.

Create `search.html`. This is the page visitors type their search query into.

You could have the search box in your layout so it's on every page. I've done it this way to keep it simple for the tutorial.

Add this content to `search.html`:

{% highlight liquid %}
{% raw %}
---
layout: default
---

<form action="get" id="site_search">
  <label for="search_box">Search</label><input type="text" id="search_box">
  <input type="submit" value="search">
</form>

<ul id="results"></ul>
{% endraw %}
{% endhighlight %}

We'll also create `/js/search.js` to hold our search Javascript.

Download the minified version from [lunr.js](http://lunrjs.com/).

Include these files and JQuery below the form in `search.html`:

{% highlight html %}
{% raw %}
...
<script src="/js/lunr.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<script src="/js/search.js"></script>
...
{% endraw %}
{% endhighlight %}

`/js/search.js` will perform three tasks:

* Load search data
* Search
* Display results

I'll go over the sections of code then show you the whole file.

Let's start with loading the search data:

{% highlight javascript %}
{% raw %}
// Initalize lunr with the fields it will be searching on. I've given title
// a boost of 10 to indicate matches on this field are more important.
window.idx = lunr(function () {
  this.field('id');
  this.field('title', { boost: 10 });
  this.field('author');
  this.field('category');
});

// Download the data from the JSON file we generated
window.data = $.getJSON('/search_data.json');

// Wait for the data to load and add it to lunr
window.data.then(function(loaded_data){
  $.each(loaded_data, function(index, value){
    window.idx.add(
      $.extend({ "id": index }, value)
    );
  });
});
{% endraw %}
{% endhighlight %}

Performing the search:
{% highlight javascript %}
{% raw %}
// Event when the form is submitted
$("#site_search").submit(function(){
    event.preventDefault();
    var query = $("#search_box").val(); // Get the value for the text field
    var results = window.idx.search(query); // Get lunr to perform a search
    display_search_results(results); // Hand the results off to be displayed
});
{% endraw %}
{% endhighlight %}

Display the results:
{% highlight javascript %}
{% raw %}
function display_search_results(results) {
  var $search_results = $("#search_results");

  // Wait for data to load
  window.data.then(function(loaded_data) {

    // Are there any results?
    if (results.length) {
      $search_results.empty(); // Clear any old results

      // Iterate over the results
      results.forEach(function(result) {
        var item = loaded_data[result.ref];

        // Build a snippet of HTML for this result
        var appendString = '<li><a href="' + item.url + '">' + item.title + '</a></li>';

        // Add it to the results
        $search_results.append(appendString);
      });
    } else {
      $search_results.html('<li>No results found</li>');
    }
  });
}
{% endraw %}
{% endhighlight %}

The whole `/js/search.js` looks like this:

{% highlight javascript %}
{% raw %}
jQuery(function() {
  // Initalize lunr with the fields it will be searching on. I've given title
  // a boost of 10 to indicate matches on this field are more important.
  window.idx = lunr(function () {
    this.field('id');
    this.field('title', { boost: 10 });
    this.field('author');
    this.field('category');
  });

  // Download the data from the JSON file we generated
  window.data = $.getJSON('/search_data.json');

  // Wait for the data to load and add it to lunr
  window.data.then(function(loaded_data){
    $.each(loaded_data, function(index, value){
      window.idx.add(
        $.extend({ "id": index }, value)
      );
    });
  });

  // Event when the form is submitted
  $("#site_search").submit(function(){
      event.preventDefault();
      var query = $("#search_box").val(); // Get the value for the text field
      var results = window.idx.search(query); // Get lunr to perform a search
      display_search_results(results); // Hand the results off to be displayed
  });

  function display_search_results(results) {
    var $search_results = $("#search_results");

    // Wait for data to load
    window.data.then(function(loaded_data) {

      // Are there any results?
      if (results.length) {
        $search_results.empty(); // Clear any old results

        // Iterate over the results
        results.forEach(function(result) {
          var item = loaded_data[result.ref];

          // Build a snippet of HTML for this result
          var appendString = '<li><a href="' + item.url + '">' + item.title + '</a></li>';

          // Add it to the results
          $search_results.append(appendString);
        });
      } else {
        $search_results.html('<li>No results found</li>');
      }
    });
  }
});
{% endraw %}
{% endhighlight %}

### TapirGo

TapirGo is free, third party service provided by [80Beans](http://www.80beans.com/) for searching RSS feeds.

It's simple to set up and fast, even for large indexes. However, all your data must be in an RSS Feed and you don't have as much control over how content is presented.

I'll assume you've got at RSS Feed set up for your Jekyll site. If you haven't, check out our [RSS Feed tutorial](/tutorials/rss-feed/).

Head over to [TapirGo](http://tapirgo.com/) and sign up for a free account. You'll need to enter the URL of your RSS Feed and your email address.

![Tapirgo](/img/tutorials/search/tapirgo.png)

Create `search.html` with the following content:

{% highlight html %}
{% raw %}
<script src="/jquery-tapir.min.js"></script>
<script type="text/javascript">
jQuery(function() {
  $('#search_results').tapir({'token': 'YOUR_TOKEN_HERE'});
});
</script>

<form id="site_search" method="get" action="search.html">
  <label for="search_box">Search</label><input type="text" id="search_box" name="query">
  <input type="submit" value="search">
</form>

<ul id="search_results"></ul>
{% endraw %}
{% endhighlight %}

Replace YOUR_TOKEN_HERE with the token Tapirgo gives you when you sign up.

That's it! The full results of the search query will display on your site.

### Google Search

This is the simplest method to implement. Google provides a search box you can embed in your website. It's fast and provides good results. The downside is you don't have as much control over what's actually being searched. There's also advertising and a limited number of queries per day on the free plan.

Create a new [Google Custom Search Engine](https://cse.google.com/cse/create/new).

![Google Custom Search Engine](/img/tutorials/search/cse.png)

On the next page click "Get Code"

![Google Custom Search Engine 2](/img/tutorials/search/cse_2.png)

Copy and paste that code into your website.

Enter a query into the search box and it will pop up with the results.
