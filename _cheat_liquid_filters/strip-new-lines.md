---
title: strip_new_lines
description: "Strip all new line characters from the input string."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "Hello
there" | strip_new_lines }}
~~~
{% endraw %}

##### Output

~~~html
Hello there
~~~
