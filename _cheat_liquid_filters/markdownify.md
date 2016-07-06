---
title: "markdownify"
description: "Convert a Markdown-formatted string into HTML."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "Hello **Jekyll**" | markdownify }}
~~~
{% endraw %}

##### Output

~~~html
Hello <strong>Jekyll</strong>
~~~
