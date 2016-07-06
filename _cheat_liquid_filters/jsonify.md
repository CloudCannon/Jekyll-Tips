---
title: "jsonify"
description: "Convert Hash or Array to JSON."
category: Array
---
##### Input

{% raw %}
~~~liquid
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | jsonify }}
~~~
{% endraw %}

##### Output

~~~html
["a","b","c"]
~~~
