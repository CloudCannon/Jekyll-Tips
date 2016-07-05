---
title: "posts"
description: "A reverse chronological list of all Posts."
---
##### Input

{% highlight liquid %}
{% raw %}
{% for p in site.posts %}
  {{ p.url }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
/2016/01/03/goodbye-world.html
/2016/01/02/im-fleeting.html
/2016/01/01/hello-world.html
{% endhighlight %}
