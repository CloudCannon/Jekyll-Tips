---
title: "array_to_sentence_string"
description: "Append characters to a string."
category: Array
---
##### Input
{% raw %}
~~~liquid
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | array_to_sentence_string }}
~~~
{% endraw %}

##### Output

~~~html
a, b, and c
~~~
