---
title: Advanced Topics
order: 12
---
In the effort to make this guide as easy as possible we've glossed over some topics. This advanced section is a chance to take a deeper dive on these topics.

### Collections vs Front Matter vs Data Files

There're many ways of adding data to Jekyll you might be wondering when do I use each one? It's not always clear but we have a few rules to help us decide:

* If the data is already in a CSV, YML, JSON or you would usually store that information in one of those file formats, use a Data File.
* If you need to order data in a non-sortable way and that data only needs to be used on a single page, use an array in Front Matter.
* Otherwise use a Collection. Collections are the most flexible method and is usually the best choice.

### RSS Feed

Blogs usually have an RSS feed to push content out to their readers. Adding one to a Jekyll Blog is super simple.

Create a file in the root of the site called `feed.xml` with the following contents:

{% highlight xml %}
{% raw %}
---
---
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
  <channel>
    <title>{{ site.name | xml_escape }} - Articles</title>
    <description>{% if site.description %}{{ site.description | xml_escape }}{% endif %}</description>
    <link>
    {{ site.url }}</link>
    {% for post in site.posts %}
      {% unless post.link %}
      <item>
        <title>{{ post.title | xml_escape }}</title>
        {% if post.excerpt %}
          <description>{{ post.excerpt | xml_escape }}</description>
        {% else %}
          <description>{{ post.content | xml_escape }}</description>
        {% endif %}
        <pubDate>{{ post.date | date: "%a, %d %b %Y %H:%M:%S %z" }}</pubDate>
        <link>
        {{ site.url }}{{ post.url }}</link>
        <guid isPermaLink="true">{{ site.url }}{{ post.url }}</guid>
      </item>
      {% endunless %}
    {% endfor %}
  </channel>
</rss>
{% endraw %}
{% endhighlight %}

The empty Front Matter is important here because it tells Jekyll we're using Liquid. This script goes through all the blog posts and outputs them in the RSS XML format.

There are a few variables we need to define, like `site.name`. Open up `_config.yml` and add this YAML:

{% highlight yaml %}
name: Creative Agency
description: We are a creative agency who provides web design, SEO, content and social services.
url: http://creative.com
{% endhighlight %}

We just need to add a link to the RSS feed to `<head>` in `_layouts/default.html`:

{% highlight html %}
<link rel="alternate" type="application/rss+xml" title="My Site RSS" href="/feed.xml" />
{% endhighlight %}

### Generate a page for Collections

In the services example earlier in the guide, you might want to generate a separate page for each service. Jekyll makes this easy.

Change `_config.yml` to:

{% highlight yaml %}
collections:
  services:
    output: true
defaults:
  -
    scope:
      path: ""
      type: "services"
    values:
      layout: "post"
{% endhighlight %}

We would also need to add a layout to each collection item. Instead of doing this I've set a default layout for the Services collection.

We just need to link to the generated page in `services.html`:

{% highlight html %}
{% raw %}
...
{% for service in site.services %}
  <div class="col-lg-3 col-md-6 text-center">
    <div class="service-box">
      <img src="{{ service.image_path }}" alt="{{ service.title }}"/>
      <h3><a href="{{ service.url }}">{{ service.title }}</a></h3>
      <p class="text-muted">{{ service.content | truncatewords: 10 }}</p>
    </div>
  </div>
{% endfor %}
...
{% endraw %}
{% endhighlight %}

I've also limited the content on the page to 10 words using a filter: `{% raw %}{{ service.content | truncatewords: 10 }}{% endraw %}`. Filters allow you to manipulate content as its output. You can find more filters [here](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers).

### Pagination

As a blog grows the list of posts can get unwieldy. Jekyll allows us to split the list of blog posts into multiple pages using pagination.

To enable pagination open **_config.yml** and set the paginate variable. This is how many items you want on each page:

{% highlight yaml %}
...
paginate: 5
paginate_path: "/blog/page:num"
...
{% endhighlight %}

We also need to move and rename `blog.html` to `/blog/index.html`. We need to do this because of how the pagination urls are going to work. They'll be named something like `/blog/page2`.

Now that we've moved the file we'll also need to update the link in `_includes/nav.html`.

{% highlight html %}
{% raw %}
...
<li {% if page.url == "/blog/index.html" %} class="active" {% endif %}>
  <a href="/blog/">Blog</a>
</li>
...
{% endraw %}
{% endhighlight %}

Finally, we need to update `/blog/index.html` to use pagination:

{% highlight html %}
{% raw %}
---
layout: default
title: Blog
---
<section class="bg-dark">
  <div class="text-center">
    <h1>Blog</h1>
  </div>
</section>

<section>
  <div class="container">
    <div class="row">
      <div class="text-center">
        <ul style="list-style-position: inside">
           {% for post in paginator.posts %}
             <li>
               <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%d %B %Y" }}
             </li>
           {% endfor %}
        </ul>
      </div>
    </div>
  </div>
</section>

<nav>
  <ul class="pager">
    {% if paginator.previous_page %}
      <li><a href="{{ paginator.previous_page_path }}">Previous</a></li>
    {% endif %}

    {% if paginator.next_page %}
      <li><a href="{{ paginator.next_page_path }}">Next</a></li>
    {% endif %}
  </ul>
</nav>
{% endraw %}
{% endhighlight %}

Jekyll makes a `paginator` variable available which does most of the work splitting it up into pages. I also added links to the previous/next page at the bottom.

### Better Navigation

One way to make the navigation code less repetitive is to pull in the links from another source. Let's try using a CSV files.

Create `_data/nav.csv` with the following contents:

{% highlight text %}
name,link
About,/about.html
Services,/services.html
Portfolio,/portfolio.html
Blog,/blog/index.html
Contact,/contact.html
{% endhighlight %}

Now we just need to iterate over this CSV in `_includes/nav.html`:

{% highlight html %}
{% raw %}
...
<ul class="nav navbar-nav navbar-right">
  {% for nav_item in site.data.nav %}
    <li {% if page.url == nav_item.link %} class="active" {% endif %}>
      <a href="{{ nav_item.link }}">{{ nav_item.name }}</a>
    </li>
  {% endfor %}
</ul>
...
{% endraw %}
{% endhighlight %}
