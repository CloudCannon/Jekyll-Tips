---
title: "pages"
description: "A list of all Pages."
---
##### Input

{% raw %}
~~~liquid
{% for p in site.pages %}
  {{ p.path }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
about.html
contact.html
index.html
site-map.xml
~~~
