---
title: "split"
description: "Divide a string into an array."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "a~b" | split:"~" }}
~~~
{% endraw %}

##### Output

~~~html
['a', 'b']
~~~
