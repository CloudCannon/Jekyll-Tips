---
title: "replace_first"
description: "Replaces only the first occurrence of a substring from a string."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ 'I really really like Jekyll' | replace_first: 'really', 'kinda' }}
~~~
{% endraw %}

##### Output

~~~html
I kinda really like Jekyll
~~~
