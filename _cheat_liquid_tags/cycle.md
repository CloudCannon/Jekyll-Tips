---
title: "cycle"
description: "Loops through a group of strings and outputs them in the order that they were passed as parameters."
category: Iteration
---

`cycle` must be used within a for loop block.

##### Input

{% raw %}
~~~liquid
{% for i in (1..5) %}
  {% cycle 'red', 'blue', 'yellow' %}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~liquid
red blue yellow red blue
~~~
