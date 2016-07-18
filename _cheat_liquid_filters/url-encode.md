---
title: "url_encode"
description: "Encodes any characters unsafe for a URL."
category: String
version: 3
---
##### Input
{% raw %}
~~~liquid
{{ "john@example.com" | url_encode }}
~~~
{% endraw %}

##### Output

~~~html
john%40example.com
~~~
