---
description: "A subset of `site.static_files` listing those which end in `.html`."
---
##### Input

{% raw %}
~~~liquid
{% for p in site.html_files %}
  {{ p.path }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
about.html contact.html index.html
~~~
