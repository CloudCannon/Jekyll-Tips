---
title: "tags._tag_"
description: "The list of all Posts with a particular tag."
---
##### Input

{% highlight liquid %}
{% raw %}
{% for p in site.tags.sad %}
  {{ p.url }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
/2016/01/03/goodbye-world.html
/2016/01/02/im-fleeting.html
{% endhighlight %}
