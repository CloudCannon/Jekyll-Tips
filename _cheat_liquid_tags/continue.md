---
title: "continue"
description: "Causes the loop to skip the current iteration."
category: Iteration
---
##### Input
{% raw %}
~~~liquid
{% for i in (1..5) %}
  {% if i == 3 %}
    {% continue %}
  {% else %}
    {{ i }}
  {% endif %}
{% endfor %}
~~~
{% endraw %}

##### Output
~~~liquid
1 2 4 5
~~~
