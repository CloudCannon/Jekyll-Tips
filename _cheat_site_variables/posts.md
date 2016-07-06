---
title: "posts"
description: "A reverse chronological list of all Posts."
---
##### Input

{% raw %}
~~~liquid
{% for p in site.posts %}
  {{ p.url }}
{% endfor %}
~~~
{% endraw %}

##### Output

~~~html
/2016/01/03/goodbye-world.html
/2016/01/02/im-fleeting.html
/2016/01/01/hello-world.html
~~~
