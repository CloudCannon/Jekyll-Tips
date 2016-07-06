---
title: "comment"
description: Don't output the contained text.
category: Other
---
##### Input

{% raw %}
~~~liquid
My name is {% comment %}Mr{% endcomment %} Jekyll
~~~
{% endraw %}

##### Output

~~~html
My name is Jekyll
~~~
