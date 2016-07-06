---
title: "tags._tag_"
description: "The list of all Posts with a particular tag."
---
##### Input

{% raw %}
~~~liquid
{% for p in site.tags.sad %}
  {{ p.url }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
/2016/01/03/goodbye-world.html
/2016/01/02/im-fleeting.html
~~~
