---
description: "Removes all newlines from the input"
---
##### Input
{% raw %}
~~~liquid
{{ "Jekyll \n be" | strip_new_lines }}
~~~
{% endraw %}

##### Output

~~~html
	Jekyll is cool
~~~
