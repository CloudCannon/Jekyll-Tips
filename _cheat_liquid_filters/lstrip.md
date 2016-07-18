---
title: "lstrip"
description: "Removes whitespace characters from the beginning of a string."
category: String
version: 3
---
##### Input
{% raw %}
~~~liquid
{{ '          I love Jekyll!          ' | lstrip }}
~~~
{% endraw %}

##### Output

~~~html
I love Jekyll!          
~~~
