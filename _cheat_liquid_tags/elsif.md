---
title: "elsif"
description: "Adds more conditions to an `if` or `unless` block."
category: Control Flow
---
##### Input

{% raw %}
~~~liquid
<!-- page.name is set to "contact" -->
{% if page.name == 'about' %}
  About Page
{% elsif page.name == 'contact' %}
  Contact Page
{% else %}
  Other Page
{% endif %}
~~~
{% endraw %}

##### Output

~~~html
Contact Page
~~~
