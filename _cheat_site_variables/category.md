---
title: "categories._category_"
description: "The list of all Posts in a category."
---
##### Input

{% highlight liquid %}
{% raw %}
{% for p in site.categories.news %}
  {{ p.url }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
/2016/01/03/goodbye-world.html
/2016/01/01/hello-world.html
{% endhighlight %}
