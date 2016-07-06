---
title: "decrement"
description: "Creates a new variable and every time it's called the value decreases by 1, with the initial value being -1."
category: Iteration
---
##### Input
{% raw %}
~~~liquid
{% decrement my_variable %}
{% decrement my_variable %}
{% decrement my_variable %}
~~~
{% endraw %}

##### Output

~~~liquid
-1
-2
-3
~~~

Like `increment`, variables declared inside decrement are independent from variables created through assign or capture.
