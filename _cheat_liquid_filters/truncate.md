---
title: "truncate"
description: "Truncate a string down to x characters."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "I love Jekyll" | truncate: 12 }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
I love Je...
{% endhighlight %}
