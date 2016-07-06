---
title: "limit"
description: "Restrict how many items are looped through."
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is [1, 2, 3, 4, 5] -->
{% for item in page.my_array limit: 2 %}
  {{ item }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
1 2
~~~
