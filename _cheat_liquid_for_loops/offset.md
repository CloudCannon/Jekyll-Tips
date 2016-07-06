---
title: "offset"
description: "Start looping from the nth item."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is [1, 2, 3, 4, 5] -->
{% for item in page.my_array offset: 2 %}
  {{ item }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
3 4 5
~~~
