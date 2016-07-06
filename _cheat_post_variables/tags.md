---
title: "tags"
description: "The list of tags to which this post belongs."
---
##### Input

{% raw %}
~~~liquid
<!-- tags is set to
  tags:
    - HTML
    - CSS
-->
{{ page.tags | array_to_sentence_string  }}
~~~
{% endraw %}

##### Output

~~~html
HTML and CSS
~~~
