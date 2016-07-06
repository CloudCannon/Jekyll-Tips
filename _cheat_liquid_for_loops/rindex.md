---
title: "rindex"
description: "Outputs the number of iterations left."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.rindex }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
3 2 1
~~~
