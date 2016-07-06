---
title: "reversed"
description: "Reverses the order."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is [1, 2, 3, 4, 5] -->
{% for item in page.my_array reversed %}
  {{ item }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
5 4 3 2 1
~~~
