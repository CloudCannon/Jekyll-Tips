---
title: "static_files"
description: "A list of all static files (i.e. files not processed by Jekyll's converters or the Liquid renderer)."
---
##### Input

{% raw %}
~~~liquid
{% for file in site.static_files %}
  {{ file.path }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
/css/style.css
/js/my-script.js
~~~
