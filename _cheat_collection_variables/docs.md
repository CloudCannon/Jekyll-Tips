---
title: "docs"
description: "An array of the collection's documents."
---
##### Input

{% highlight liquid %}
{% raw %}
{{ site.my_collection.docs.first.url }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
/my_collection/item.html
{% endhighlight %}
