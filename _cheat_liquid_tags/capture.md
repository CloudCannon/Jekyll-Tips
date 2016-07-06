---
title: "capture"
description: "Captures the string inside of the opening and closing tags and assigns it to a variable."
category: Variable
---
##### Input

{% raw %}
~~~liquid
{% capture my_variable %}
  Captured text.
{% endcapture %}

{{ my_variable }}
~~~
{% endraw %}

##### Output

~~~html
Captured text.
~~~
