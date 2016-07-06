---
title: "relative_path"
description: "The path to the document's source file relative to the site source."
---
##### Input

{% raw %}
~~~liquid
{{ site.my_collection.first.relative_path }}
~~~
{% endraw %}

##### Output

~~~html
_my_collection/item.md
~~~
