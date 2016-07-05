---
title: "split"
description: "Divide a string into an array."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "a~b" | split:"~" }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
['a', 'b']
{% endhighlight %}
