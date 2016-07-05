---
title: "relative_path"
description: "The path to the document's source file relative to the site source."
---
##### Input

{% highlight liquid %}
{% raw %}
{{ site.collections.my_collection.relative_path }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
_my_collection
{% endhighlight %}
