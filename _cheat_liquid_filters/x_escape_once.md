---
description: "Returns an escaped version of html without affecting existing escaped entities"
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "<p>Jekyll &amp; Hyde</p>" | escape_once }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
&amp;lt;p&amp;gt;Jekyll &amp; Hyde&amp;lt;/p&amp;gt;
{% endhighlight %}
