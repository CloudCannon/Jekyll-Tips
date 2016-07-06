---
title: "slice"
description: "returns a substring, starting at the specified index."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "hello" | slice: 0 }}
{{ "hello" | slice: 1 }}
{{ "hello" | slice: 1, 3 }}
~~~
{% endraw %}

##### Output

~~~html
h
e
ell
~~~
