---
title: "related_posts"
description: "If the page being processed is a Post, this contains a list of up to ten related Posts. By default, these are the ten most recent posts."
---
##### Input

{% raw %}
~~~liquid
<!-- run on /_posts/2016-01-01-hello-world.md -->
{% for p in site.related_posts %}
  {{ p.title }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
Goodbye World
Im Fleeting
~~~
