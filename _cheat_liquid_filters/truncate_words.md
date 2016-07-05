---
title: "truncatewords"
description: "Truncate string down to x words."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "I love Jekyll" | truncatewords: 2 }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
I love...
{% endhighlight %}
