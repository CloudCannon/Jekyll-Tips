---
title: "unless"
description: "Similar to `if`, but executes a block of code only if a certain condition is **not** met."
category: Control Flow
---
##### Input

{% raw %}
~~~liquid
<!-- page.name is set to "about" -->
{% unless page.name == "contact" %}
  It's not the contact page
{% endunless %}
~~~
{% endraw %}

##### Output

~~~html
It's not the contact page
~~~

Which is the same as doing:

{% raw %}
~~~liquid
{% if page.name != "contact" %}
  It's not the contact page
{% endif %}
~~~
{% endraw %}
