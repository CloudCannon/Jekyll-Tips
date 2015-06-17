---
title: SEO
heading: SEO in Jekyll
---
Users coming from Wordpress commonly ask how to do SEO in Jekyll. In Jekyll you have more control over SEO than a Wordpress plugin can give you.

For the basis of this tutorial I'll be referencing topics outlined in Google's [Search Engine Optimization
Starter Guide](http://static.googleusercontent.com/media/www.google.com/en/us/webmasters/docs/search-engine-optimization-starter-guide.pdf).

We'll be covering the `<title>` and `<meta>` description tags, improving the structure of URLs, adding a site map and custom 404 pages.

### Title and Descriptions

We can make `<title>` and `<meta>` description tags easily editable using Front Matter.

For `<title>` we'll output the a title from a Front Matter variable if it exists, otherwise fall back to a default:

{% highlight liquid %}
{% raw %}
...
<title>
  {% if page.title %}
    {{ page.title }}
  {% else %}
    Default Page Title
  {% endif %}
</title>
...
{% endraw %}
{% endhighlight %}

For `<meta>` description, we'll output the meta tag only if the Front Matter variable exists:

{% highlight liquid %}
{% raw %}
...
{% if page.description %}
  <meta name="description" content="{{ page.description}}" />
{% endif %}
...
{% endraw %}
{% endhighlight %}

Now we set those variables in the Front Matter for each HTML page like this:

{% highlight liquid %}
{% raw %}
---
title: Creative Hub - Blog
description: A blog with the latest trends and news in Web Design
---
...
{% endraw %}
{% endhighlight %}

If you're using [CloudCannon](http://cloudcannon.com), your non-technical users can easily update the Front Matter:

![Front Matter on CloudCannon](/img/tutorials/seo/front_matter.png)


### Improving the Structure of URLs

Using Permalinks you can control how Jekyll builds your URLs. For SEO, Google recommends using descriptive keywords in your URL.

Let's say you have an HTML page `/red.html` but you wanted the URL to be `/cups/red/`, you could see the permalink in the Front Matter like this:

{% highlight liquid %}
{% raw %}
---
permalink: /cups/red/
---
...
{% endraw %}
{% endhighlight %}

You could also just place the rename the file from `/red.html` to `/cups/red/index.html`, Jekyll gives you the power to organize your site however you'd like.

A more useful example is changing the permalink for blog posts. Just add this line to `_config.yml`:

{% highlight yaml %}
{% raw %}
...
permalink: /blog/:year/:month/:day/:title/
...
{% endraw %}
{% endhighlight %}


You can also change the permalink for an entire Collection:

{% highlight yaml %}
{% raw %}
...
collections:
  products:
    output: true
    permalink: "/:collection/:title/"
...
{% endraw %}
{% endhighlight %}

### Sitemap

We can generate a sitemap for our site using a script from [David Ensinger](http://davidensinger.com/2013/11/building-a-better-sitemap-xml-with-jekyll/).

Create `/sitemap.xml` with the following content:

{% highlight liquid %}
{% raw %}
---
layout: null
sitemap:
  exclude: 'yes'
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {% for post in site.posts %}
    {% unless post.published == false %}
    <url>
      <loc>{{ site.url }}{{ post.url }}</loc>
      {% if post.sitemap.lastmod %}
        <lastmod>{{ post.sitemap.lastmod | date: "%Y-%m-%d" }}</lastmod>
      {% elsif post.date %}
        <lastmod>{{ post.date | date_to_xmlschema }}</lastmod>
      {% else %}
        <lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
      {% endif %}
      {% if post.sitemap.changefreq %}
        <changefreq>{{ post.sitemap.changefreq }}</changefreq>
      {% else %}
        <changefreq>monthly</changefreq>
      {% endif %}
      {% if post.sitemap.priority %}
        <priority>{{ post.sitemap.priority }}</priority>
      {% else %}
        <priority>0.5</priority>
      {% endif %}
    </url>
    {% endunless %}
  {% endfor %}

  {% for page in site.pages %}
    {% assign split_path = page.path | split: "." %}
    {% assign extension = split_path | last %}

    {% if page.sitemap.exclude != "yes" and extension == "html" and page.path != "/404.html" %}
    <url>
      <loc>{{ site.url }}{{ page.permalink | remove: "index.html" }}</loc>
      {% if page.sitemap.lastmod %}
        <lastmod>{{ page.sitemap.lastmod | date: "%Y-%m-%d" }}</lastmod>
      {% elsif page.date %}
        <lastmod>{{ page.date | date_to_xmlschema }}</lastmod>
      {% else %}
        <lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
      {% endif %}
      {% if page.sitemap.changefreq %}
        <changefreq>{{ page.sitemap.changefreq }}</changefreq>
      {% else %}
        <changefreq>monthly</changefreq>
      {% endif %}
      {% if page.sitemap.priority %}
        <priority>{{ page.sitemap.priority }}</priority>
      {% else %}
        <priority>0.3</priority>
      {% endif %}
    </url>
    {% endif %}
  {% endfor %}

  {% for collection in site.collections %}
    {% if collection[1].output %}
      {% for doc in collection[1].docs %}
        <url>
          <loc>{{ site.url }}{{ doc.url | remove: "index.html" }}</loc>
          {% if doc.sitemap.lastmod %}
            <lastmod>{{ doc.sitemap.lastmod | date: "%Y-%m-%d" }}</lastmod>
          {% elsif doc.date %}
            <lastmod>{{ doc.date | date_to_xmlschema }}</lastmod>
          {% else %}
            <lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
          {% endif %}
          {% if doc.sitemap.changefreq %}
            <changefreq>{{ doc.sitemap.changefreq }}</changefreq>
          {% else %}
            <changefreq>monthly</changefreq>
          {% endif %}
          {% if doc.sitemap.priority %}
            <priority>{{ doc.sitemap.priority }}</priority>
          {% else %}
            <priority>0.3</priority>
          {% endif %}
        </url>
      {% endfor %}
    {% endif %}
  {% endfor %}
</urlset>
{% endraw %}
{% endhighlight %}

By default this will include all pages and blog posts on your website. You can exclude pages and configure properties like the priority using Front Matter:

{% highlight liquid %}
{% raw %}
sitemap:
  lastmod: 2015-01-23
  priority: 0.7
  changefreq: monthly
  exclude: yes
{% endraw %}
{% endhighlight %}

We also need to add the domain of the website to `_config.yml`:

{% highlight yaml %}
{% raw %}
...
url: http://mysite.com
...
{% endraw %}
{% endhighlight %}

### Custom 404 Pages

This is more of a best practice. Custom 404 Pages in Jekyll can help users navigate your site if they've gone to a page that doesn't exist. Create `404.html` with the content for your 404 page. You can use Front Matter, liquid and layouts as normal.

[GitHub Pages](https://pages.github.com), [CloudCannon](http://cloudcannon.com) and the Jekyll Server will show 404.html when they can't find a page. Any other services may require configuration to get custom 404 pages working.


### Tips for Content

Good content is the key to SEO. With a few simple rules you can ensure all your content is working towards a high ranking in search enginges:

* Search Engines love fresh content
* Search Engines don't like duplicate content
* Images should always have an [alt attribute](http://www.w3schools.com/tags/att_img_alt.asp)
* Use descriptive text when linking: _Bad_: [click here](http://static.googleusercontent.com/media/www.google.com/en/us/webmasters/docs/search-engine-optimization-starter-guide.pdf) for the Google SEO Starter Guide. _Good_: Download the [Google SEO Starter Guide](http://static.googleusercontent.com/media/www.google.com/en/us/webmasters/docs/search-engine-optimization-starter-guide.pdf).
* If you delete a page, make it redirect somewhere else relevant. You can do this on [CloudCannon](http://cloudcannon.com) using [301 redirects](http://docs.cloudcannon.com/#common_tasks6_301_redirectshtml).
