---
description: "Returns an escaped version of html without affecting existing escaped entities"
---
##### Input
{% raw %}
~~~liquid
{{ "<p>Jekyll &amp; Hyde</p>" | escape_once }}
~~~
{% endraw %}

##### Output

~~~html
&amp;lt;p&amp;gt;Jekyll &amp; Hyde&amp;lt;/p&amp;gt;
~~~
