---
source: https://github.com/snaptortoise/jekyll-rss-feeds/blob/master/feed.articles.xml
author:
  name: snaptortoise
  link: https://github.com/snaptortoise
title: RSS Feed
heading: RSS Feed in Jekyll
---

Blogs usually have an RSS feed to push content out to their readers. Adding a RSS Feed to a Jekyll Blog is super simple.

Create a file in the root of the site called `feed.xml` with the following contents:

{% highlight xml %}
{% raw %}
---
layout: null
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

This script goes through all the blog posts and outputs them in the RSS XML format.

There are a few variables we need to define, like `site.name`. Open up `_config.yml` and add this YAML:

{% highlight yaml %}
...
name: Creative Agency
description: We are a creative agency who provides web design, SEO, content and social services.
url: http://creative.com
...
{% endhighlight %}

We just need to add a link to the RSS feed to `<head>` which is probably in `_layouts/default.html`:

{% highlight html %}
...
<link rel="alternate" type="application/rss+xml" title="My Site RSS" href="/feed.xml" />
...
{% endhighlight %}
