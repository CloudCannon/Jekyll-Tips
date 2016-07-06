---
title: "remove_first"
description: "Removes only the first occurrence of a substring from a string."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ 'I really really like Jekyll' | remove_first: 'really' }}
~~~
{% endraw %}

##### Output

~~~html
I really like Jekyll
~~~
