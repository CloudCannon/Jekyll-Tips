---
source: https://github.com/mdo/jekyll-snippets/blob/master/atom.xml
author:
  name: MDO
  link: https://github.com/mdo
title: Atom Feed
heading: Atom Feed in Jekyll
---

An Atom feed allows readers to subscribe to the latest posts on your blog. Adding an Atom Feed to a Jekyll website is simple.

Create `atom.xml` to the root of the website with the following contents:

{% highlight xml %}
{% raw %}
---
layout: null
---

<?xml version="1.0" encoding="utf-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>{{ site.name }}</title>
  <link href="{{ site.url }}/atom.xml" rel="self" />
  <link href="{{ site.url }}/"/>
  <updated>{{ site.time | date_to_xmlschema }}</updated>
  <id>{{ site.url }}</id>
  <author>
    <name>{{ site.author.name }}</name>
    <email>{{ site.author.email }}</email>
  </author>
  {% for post in site.posts %}
    <entry>
      <title>{{ post.title }}</title>
      <link href="{{ site.url }}{{ post.url }}" />
      <updated>{{ post.date | date_to_xmlschema }}</updated>
      <id>{{ site.url }}{{ post.id }}</id>
      <content type="html">{{ post.content | xml_escape }}</content>
    </entry>
  {% endfor %}
</feed>
{% endraw %}
{% endhighlight %}

This iterates over all your blog posts and prints them out in XML. Now we need to add the site variables to `_config.yml`:

{% highlight yaml %}
...
name: Creative Agency
url: http://creative.com
author:
  name: Mike
  email: mike@creative.com
...
{% endhighlight %}

And finally add a link to `<head>` which is probably in `_layouts/default.html` :

{% highlight html %}
...
<link rel="alternate" type="application/atom+xml" title="The Creative Blog" href="/atom_feed.xml" />
...
{% endhighlight %}
