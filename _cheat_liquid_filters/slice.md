---
title: "slice"
description: "returns a substring, starting at the specified index."
category: String
version: 3
---
##### Input
{% raw %}
~~~liquid
{{ "hello" | slice: 0 }}
{{ "hello" | slice: 1 }}
{{ "hello" | slice: 1, 3 }}
{{ "hello" | slice: -2 }}
{{ "hello" | slice: -3, 2 }}
~~~
{% endraw %}

##### Output

~~~html
h
e
ell
l
ll
~~~
