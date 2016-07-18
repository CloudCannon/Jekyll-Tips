---
title: "uniq"
description: "Removes duplicate elements from an array."
category: Array
version: 3
---
##### Input
{% raw %}
~~~liquid
<!-- page.my_array is ['cat', 'dog', 'mouse', 'cat'] -->
{{ page.my_array | uniq }}
~~~
{% endraw %}

##### Output

~~~html
'cat', 'dog', 'mouse'
~~~
