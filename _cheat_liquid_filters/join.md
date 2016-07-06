---
title: "join"
description: "Joins an array with the specified character."
category: Array
---
##### Input
{% raw %}
~~~liquid
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | join: ', ' }}
~~~
{% endraw %}

##### Output

~~~html
a, b, c
~~~
