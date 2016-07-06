---
title: "if"
description: "Executes a block of code only if a certain condition is met."
category: Control Flow
---
##### Input

{% raw %}
~~~liquid
<!-- page.name is set to "about" -->
{% if page.name == 'about' %}
  About Page
{% endif %}
~~~
{% endraw %}

##### Output

~~~html
  About Page
~~~
