---
title: "break"
description: "Causes the loop to stop iterating."
category: Iteration
---
##### Input
{% raw %}
~~~liquid
{% for i in (1..5) %}
  {% if i == 3 %}
    {% break %}
  {% else %}
    {{ i }}
  {% endif %}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~liquid
1 2
~~~
