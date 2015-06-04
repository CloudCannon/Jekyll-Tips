---
title: Advanced Topics
order: 13
---
In the effort to make this guide as easy as possible we've glossed over some topics. This advanced section is a chance to take a deeper dive on these topics.

### Collections vs Front Matter vs Data Files

There're many ways of adding data to Jekyll you might be wondering when do I use each one? It's not always clear but we have a few rules to help us decide:

* If the data is already in a CSV, YML, JSON or you would usually store that information in one of those file formats, use a Data File.
* If you need to order data in a non-sortable way and that data only needs to be used on a single page, use an array in Front Matter.
* Otherwise use a Collection. Collections are the most flexible method and is usually the best choice.

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

### Conclusion

Hopefully this guide has given you a good foundation. Now you can go out and populate the internet with beautiful Jekyll websites.

If you get stuck and need help the offical Jekyll website has excellent [documentation](http://jekyllrb.com/docs/home/). The community at [talk.jekyllrb.com](http://talk.jekyllrb.com) is also a great resource.

Happy Jekylling!
