---
title: "categories"
description: "The list of categories to which this post belongs."
---
##### Input

{% raw %}
~~~liquid
<!-- tags is set to
  categories:
    - news
-->
{{ page.categories | array_to_sentence_string  }}
~~~
{% endraw %}

##### Output

~~~html
news
~~~
