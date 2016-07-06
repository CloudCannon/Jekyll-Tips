---
title: "escape"
description: "Returns an escaped version of html."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "<p>Jekyll</p>" | escape }}
~~~
{% endraw %}

##### Output

~~~html
&amp;lt;p&amp;gt;Jekyll&amp;lt;/p&amp;gt;
~~~
