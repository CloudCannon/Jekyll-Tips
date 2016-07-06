---
title: "else"
description: "Condition when there are no items in the array."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is [] -->
{% for item in page.my_array %}
  {{ item }}
{% else %}
  There are no items!
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
There are no items!
~~~
