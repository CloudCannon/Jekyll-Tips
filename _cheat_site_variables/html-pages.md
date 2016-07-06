---
title: "html_pages"
description: "A subset of `site.pages` listing those which end in `.html`"
---
##### Input

{% raw %}
~~~liquid
{% for p in site.html_pages %}
  {{ p.path }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
about.html
contact.html
index.html
~~~
