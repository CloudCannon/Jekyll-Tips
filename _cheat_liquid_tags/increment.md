---
title: "increment"
description: "Creates a new variable and every time it's called the value increases by 1, with the initial value being 0."
category: Iteration
---
##### Input
{% raw %}
~~~liquid
{% increment my_variable %}
{% increment my_variable %}
{% increment my_variable %}
~~~
{% endraw %}

##### Output

~~~liquid
0
1
2
~~~

Variables created through the `increment` tag are independent from variables created through `assign` or `capture`.

In the example below, `my_var` is created through `assign`. The `increment` tag is then used several times on a variable with the same name. However, note that the `increment` tag does not affect the value of `my_var` that was created through `assign`.

##### Input
{% raw %}
~~~liquid
{% assign my_var = 15 %}
{% increment var %}
{% increment var %}
{% increment var %}
{{ my_var }}
~~~
{% endraw %}

##### Output
~~~liquid
0
1
2
15
~~~
