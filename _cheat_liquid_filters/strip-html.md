---
title: "strip_html"
description: "Strip all html tags from the input string."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "<p>Jekyll is cool</p>" | strip_html }}
~~~
{% endraw %}

##### Output

~~~html
Jekyll is cool
~~~
