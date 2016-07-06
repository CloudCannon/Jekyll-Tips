---
title: "first"
description: "Returns whether it's the first iteration."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is [1, 2, 3] -->
{% for item in page.my_array %}
  {% if forloop.first %}
    First!
  {% else %}
    Not first
{% endif %}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
First! Not first Not first
~~~
