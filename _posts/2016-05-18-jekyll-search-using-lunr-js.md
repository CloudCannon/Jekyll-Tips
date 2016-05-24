---
title: Jekyll Search using lunr.js
episode: 20
image_path: /img/casts/lunr-js/preview.jpg
length: 4
video_id: XTAFSDqQMko
description: Add search to your Jekyll site using lunr.js
resources:
  - name: Source code
    link: https://github.com/CloudCannon/bakery-store/tree/json
  - name: Katy Decorah's "Unconventional use cases for Jekyll"
    link: http://katydecorah.com/code/jekyllconf/
category: advanced
order: 3
---
We're adding search to our demo Bakery Store site so users can easily find relevant content. This is a small site so we can perform the search on the client side. If there were hundreds of blog posts performing the search in the backend would make more sense.

To build the search we'll use [lunr.js](http://lunrjs.com/), a client side full-text search engine. The search will work in the following steps:

1. Send the search term as a [GET parameter](http://www.w3schools.com/tags/ref_httpmethods.asp) to `search.html`.
2. `search.html` reads the GET parameter and searches through a JSON file containing all the searchable content.
3. `search.html` displays a list of search results.

First we'll create a JSON file `/search-data.json` which contains the data we want to search on. We'll create a JSON object where each post has a key of the post URL and a value of the title, author, category and URL.

{% highlight liquid %}
{% raw %}
---
layout: null
---
{
  {% for post in site.posts %}

    "{{ post.url | slugify }}": {
      "title": "{{ post.title | xml_escape }}",
      "author": "{{ post.author | xml_escape }}",
      "category": "{{ post.category | xml_escape }}",
      "url": "{{ post.url | xml_escape }}"
    }
    {% unless forloop.last %},{% endunless %}
  {% endfor %}
}
{% endraw %}
{% endhighlight %}

We'll create `/js/search.js` to hold our search Javascript and download [lunr.js](http://lunrjs.com/) to `/js/lunr.min.js`.

Now we need to create `/search.html` which has a search box, a placeholder for displaying results and includes our javascript libraries.

{% highlight html %}
{% raw %}
---
layout: default
---

<form action="/search.html" method="get" id="site_search">
  <label for="search_box">Search</label>
  <input type="text" id="search_box" name="search_term">
  <input type="submit" value="search">
</form>

<ul id="search_results"></ul>

<script src="/js/lunr.min.js"></script>
<script src="/js/search.js"></script>
{% endraw %}
{% endhighlight %}

Next we need to write the Javascript for `/js/search.js` to perform three tasks:

* Get the search term
* Perform the search
* Display the results

We'll go over the sections of code then at the end, we'll see the whole file.

***Get the search term***

Javascript doesn't have an easy way to read GET parameters so we'll add a `getParameterByName` function to do this. Don't worry if you don't understand how it works. Now we can use `getParameterByName` to get our search term.

{% highlight javascript %}
{% raw %}
...
function getParameterByName(name) {
  url = window.location.href;
  name = name.replace(/[\[\]]/g, '\\$&');
  var regex = new RegExp('[?&]' + name + '(=([^&#]*)|&|#|$)'),
    results = regex.exec(url);
  if (!results) return null;
  if (!results[2]) return '';
  return decodeURIComponent(results[2].replace(/\+/g, ' '));
}

var searchTerm = getParameterByName('search_term');
...
{% endraw %}
{% endhighlight %}

***Perform the search***

We need to add another function which doesn't matter if you don't understand the inner workings. This one is called `getJSON` and we'll use it to retrieve our `/search-data.json` file.

{% highlight javascript %}
{% raw %}
...
function getJSON(url, callback) {
  var xhr = new XMLHttpRequest();
  xhr.open('get', url, true);
  xhr.responseType = 'json';
  xhr.onload = function() {

    var status = xhr.status;

    if (status == 200) {
      callback(null, xhr.response);
    } else {
      callback(status);
    }
  };
  xhr.send();
}
...
{% endraw %}
{% endhighlight %}

If there is a search term we need to set up and configure lunr.js. This involves telling lunr about the fields we're interested and adding the search data from `/search-data.json`. Once this is set up we can perform the search.

{% highlight javascript %}
{% raw %}
...
if (searchTerm) {
  // Initalize lunr with the fields it will be searching on. I've given title
  // a boost of 10 to indicate matches on this field are more important.
  var idx = lunr(function () {
    this.field('id');
    this.field('title', { boost: 10 });
    this.field('author');
    this.field('category');
  });

  // Download the data from the JSON file we generated
  getJSON('/search-data.json', function(status, store) {
    for (var key in store) { // Add the data to lunr
      idx.add({
        'id': key,
        'title': store[key].title,
        'author': store[key].author,
        'category': store[key].category
      });
    }

    var results = idx.search(searchTerm); // Get lunr to perform a search
    displaySearchResults(results, store); // We'll write this in the next section
  });
}
...
{% endraw %}
{% endhighlight %}

***Display the results***

Now we have the results we can display them in our list.

{% highlight javascript %}
{% raw %}
...
function displaySearchResults(results, store) {
  var searchResults = document.getElementById('search_results');

  if (results.length) { // Are there any results?
    var appendString = '';

    for (var i = 0; i < results.length; i++) {  // Iterate over the results
      var item = store[results[i].ref];
      appendString += '<li><a href="' + item.url + '">' + item.title + '</a></li>';
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
    var searchResults = document.getElementById('search_results');

    if (results.length) { // Are there any results?
      var appendString = '';

      for (var i = 0; i < results.length; i++) {   // Iterate over the results
        var item = store[results[i].ref];
        appendString += '<li><a href="' + item.url + '">' + item.title + '</a></li>';
      }

      searchResults.innerHTML = appendString;
    } else {
      searchResults.innerHTML = '<li>No results found</li>';
    }
  }

  function getJSON(url, callback) {
    var xhr = new XMLHttpRequest();
    xhr.open('get', url, true);
    xhr.responseType = 'json';
    xhr.onload = function() {

      var status = xhr.status;

      if (status == 200) {
        callback(null, xhr.response);
      } else {
        callback(status);
      }
    };
    xhr.send();
  }

  function getParameterByName(name) {
    url = window.location.href;
    name = name.replace(/[\[\]]/g, '\\$&');
    var regex = new RegExp('[?&]' + name + '(=([^&#]*)|&|#|$)'),
      results = regex.exec(url);
    if (!results) return null;
    if (!results[2]) return '';
    return decodeURIComponent(results[2].replace(/\+/g, ' '));
  }

  var searchTerm = getParameterByName('search_term');

  if (searchTerm) {
    // Initalize lunr with the fields it will be searching on. I've given title
    // a boost of 10 to indicate matches on this field are more important.
    var idx = lunr(function () {
      this.field('id');
      this.field('title', { boost: 10 });
      this.field('author');
      this.field('category');
    });

    // Download the data from the JSON file we generated
    getJSON('/search-data.json', function(status, store) {
      for (var key in store) { // Add the data to lunr
        idx.add({
          'id': key,
          'title': store[key].title,
          'author': store[key].author,
          'category': store[key].category
        });
      }

      var results = idx.search(searchTerm); // Get lunr to perform a search
      displaySearchResults(results, store); // We'll write this in the next section
    });
  }
})();
{% endraw %}
{% endhighlight %}

![Search Results](/img/casts/lunr-js/results.png)

Now we can add a search box anywhere on our site by adding a form which submits to `/search.html`.

{% highlight html %}
{% raw %}
...
<form action="/search.html" method="get" id="site_search">
  <label for="search_box">Search</label>
  <input type="text" id="search_box" name="search_term">
  <input type="submit" value="search">
</form>
...
{% endraw %}
{% endhighlight %}

This technique isn't limited to blog posts, we could do the same thing for collections, data files or even static files.
