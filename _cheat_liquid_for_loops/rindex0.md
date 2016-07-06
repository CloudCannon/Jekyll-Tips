---
title: "rindex0"
description: "Outputs the number of iterations left (zero based)."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.rindex0 }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
2 1 0
~~~
