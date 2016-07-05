---
title: Jekyll search using lunr.js
episode: 20
image_path: /img/casts/lunr-js/preview.jpg
length: 5
video_id: Nebae_YEok4
description: Add search to your Jekyll site using lunr.js
resources:
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/lunrjs
  - name: lunr.js
    link: http://lunrjs.com/
  - name: Outputting JSON in Jekyll
    link: /jekyll-casts/output-json/
category: advanced
order: 3
---
We're adding search to our demo Bakery Store site so users can easily find relevant content. This is a small site so we can perform the search on the client side. If there were hundreds of blog posts performing the search in the backend would make more sense.

To build the search we'll use [lunr.js](http://lunrjs.com/), a client side full-text search engine. The search will work in the following steps:

1. Send the search term as a GET parameter to `search.html`.
2. `search.html` reads the GET parameter and searches through JSON containing the searchable content.
3. `search.html` displays a list of search results.

First we'll create `/js/search.js` to hold our search JavaScript and download [lunr.js](http://lunrjs.com/) to `/js/lunr.min.js`.

Now we need to create `/search.html` which has a search box, a placeholder for displaying results, a JSON output of all the content we want to search on and includes our JavaScript libraries.

{% highlight html %}
{% raw %}
---
layout: search
---
<form action="/search.html" method="get">
  <label for="search-box">Search</label>
  <input type="text" id="search-box" name="query">
  <input type="submit" value="search">
</form>

<ul id="search-results"></ul>

<script>
  window.store = {
    {% for post in site.posts %}
      "{{ post.url | slugify }}": {
        "title": "{{ post.title | xml_escape }}",
        "author": "{{ post.author | xml_escape }}",
        "category": "{{ post.category | xml_escape }}",
        "content": {{ post.content | strip_html | strip_newlines | jsonify }},
        "url": "{{ post.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
    {% endfor %}
  };
</script>
<script src="/js/lunr.min.js"></script>
<script src="/js/search.js"></script>
{% endraw %}
{% endhighlight %}

Next we need to write the JavaScript for `/js/search.js` to perform three tasks:

* Get the search term
* Perform the search
* Display the results

We'll go over the sections of code then at the end, we'll see the whole file.

### Get the search term

JavaScript doesn't have an easy way to read GET parameters so we'll add a `getParameterByName` function to do this. Don't worry if you don't understand how it works. Now we can use `getParameterByName` to get our search term.

{% highlight javascript %}
{% raw %}
...
function getQueryVariable(variable) {
  var query = window.location.search.substring(1);
  var vars = query.split('&');

  for (var i = 0; i < vars.length; i++) {
    var pair = vars[i].split('=');

    if (pair[0] === variable) {
      return decodeURIComponent(pair[1].replace(/\+/g, '%20'));
    }
  }
}

var searchTerm = getQueryVariable('query');
...
{% endraw %}
{% endhighlight %}

### Perform the search

If there's a search term we need to set up and configure lunr.js. This involves telling lunr about the fields we're interested and adding the search data from the JSON. Once this is set up we can perform the search.

{% highlight javascript %}
{% raw %}
...
if (searchTerm) {
  document.getElementById('search-box').setAttribute("value", searchTerm);

  // Initalize lunr with the fields it will be searching on. I've given title
  // a boost of 10 to indicate matches on this field are more important.
  var idx = lunr(function () {
    this.field('id');
    this.field('title', { boost: 10 });
    this.field('author');
    this.field('category');
    this.field('content');
  });

  for (var key in window.store) { // Add the data to lunr
    idx.add({
      'id': key,
      'title': window.store[key].title,
      'author': window.store[key].author,
      'category': window.store[key].category,
      'content': window.store[key].content
    });

    var results = idx.search(searchTerm); // Get lunr to perform a search
    displaySearchResults(results, window.store); // We'll write this in the next section
  }
}
...
{% endraw %}
{% endhighlight %}

### Display the results

Now we have the results we can display them in our list.

{% highlight javascript %}
{% raw %}
...
function displaySearchResults(results, store) {
  var searchResults = document.getElementById('search-results');

  if (results.length) { // Are there any results?
    var appendString = '';

    for (var i = 0; i < results.length; i++) {  // Iterate over the results
      var item = store[results[i].ref];
      appendString += '<li><a href="' + item.url + '"><h3>' + item.title + '</h3></a>';
      appendString += '<p>' + item.content.substring(0, 150) + '...</p></li>';
    }

    searchResults.innerHTML = appendString;
  } else {
    searchResults.innerHTML = '<li>No results found</li>';
  }
}
...
{% endraw %}
{% endhighlight %}

When we put it all together we have working search.

{% highlight javascript %}
{% raw %}
(function() {
  function displaySearchResults(results, store) {
    var searchResults = document.getElementById('search-results');

    if (results.length) { // Are there any results?
      var appendString = '';

      for (var i = 0; i < results.length; i++) {  // Iterate over the results
        var item = store[results[i].ref];
        appendString += '<li><a href="' + item.url + '"><h3>' + item.title + '</h3></a>';
        appendString += '<p>' + item.content.substring(0, 150) + '...</p></li>';
      }

      searchResults.innerHTML = appendString;
    } else {
      searchResults.innerHTML = '<li>No results found</li>';
    }
  }

  function getQueryVariable(variable) {
    var query = window.location.search.substring(1);
    var vars = query.split('&');

    for (var i = 0; i < vars.length; i++) {
      var pair = vars[i].split('=');

      if (pair[0] === variable) {
        return decodeURIComponent(pair[1].replace(/\+/g, '%20'));
      }
    }
  }

  var searchTerm = getQueryVariable('query');

  if (searchTerm) {
    document.getElementById('search-box').setAttribute("value", searchTerm);

    // Initalize lunr with the fields it will be searching on. I've given title
    // a boost of 10 to indicate matches on this field are more important.
    var idx = lunr(function () {
      this.field('id');
      this.field('title', { boost: 10 });
      this.field('author');
      this.field('category');
      this.field('content');
    });

    for (var key in window.store) { // Add the data to lunr
      idx.add({
        'id': key,
        'title': window.store[key].title,
        'author': window.store[key].author,
        'category': window.store[key].category,
        'content': window.store[key].content
      });

      var results = idx.search(searchTerm); // Get lunr to perform a search
      displaySearchResults(results, window.store); // We'll write this in the next section
    }
  }
})();
{% endraw %}
{% endhighlight %}

![Search Results](/img/casts/lunr-js/results.png)

Now we can add a search box anywhere on our site by adding a form which submits to `/search.html`.

{% highlight html %}
{% raw %}
...
<form action="/search.html" method="get">
  <label for="search-box">Search</label>
  <input type="text" id="search-box" name="query">
  <input type="submit" value="search">
</form>
...
{% endraw %}
{% endhighlight %}

This technique isn't limited to blog posts, we could do the same thing for collections, data files or even static files.
