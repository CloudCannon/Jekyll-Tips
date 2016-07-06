---
title: "length"
description: "Length of the entire loop."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.length }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
3 3 3
~~~
