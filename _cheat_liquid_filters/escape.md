---
title: "escape"
description: "Returns an escaped version of html."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "<p>Jekyll</p>" | escape }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
&amp;lt;p&amp;gt;Jekyll&amp;lt;/p&amp;gt;
{% endhighlight %}
