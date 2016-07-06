---
title: "xml_escape"
description: "Select all the objects in an array where the key has the given value."
category: String
---
##### Input
{% raw %}
~~~liquid
{{ "<p>Hi Jekyll</p>"| xml_escape }}
~~~
{% endraw %}

##### Output

~~~html
&amp;lt;p&amp;gt;Hi Jekyll&amp;lt;/p&amp;gt;
~~~
