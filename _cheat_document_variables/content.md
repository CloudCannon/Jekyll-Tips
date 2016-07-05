---
title: "content"
description: "The content of the collection item, rendered or un-rendered depending upon what Liquid is being processed and the item is."
---
##### Input

{% highlight liquid %}
{% raw %}
{{ site.my_collection.first.content }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Hello from my_collection.
{% endhighlight %}
