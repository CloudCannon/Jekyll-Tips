---
title: "date_to_long_rfc822"
description: "Convert a Date into RFC-822 format."
category: Date
---
##### Input
{% highlight liquid %}
{% raw %}
{{ site.time | date_to_rfc822 }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Mon, 07 Nov 2008 13:07:54 -0800
{% endhighlight %}
