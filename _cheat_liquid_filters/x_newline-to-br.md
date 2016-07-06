---
description: "replace each newline (\n) with a <br>"
---
##### Input
{% raw %}
~~~liquid
<!-- _/posts/2016-01-01-hello.md contains a multiple line string.  -->
{{ site.posts.first.content | newline_to_br }}
~~~
{% endraw %}

##### Output

~~~html
1
~~~
