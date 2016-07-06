---
title: "cgi_escape"
description: "Escape a string for use in a URL."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "foo,bar;baz?" | cgi_escape }}
~~~
{% endraw %}

##### Output

~~~html
foo%2Cbar%3Bbaz%3F
~~~
