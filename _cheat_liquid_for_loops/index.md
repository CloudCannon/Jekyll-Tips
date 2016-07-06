---
title: "index"
description: "index of the current iteration."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.index }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
1 2 3
~~~
