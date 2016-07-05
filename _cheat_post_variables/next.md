---
title: "next"
description: "The next post relative to the position of the current post in `site.posts`. Returns `nil` for the last entry."
---
##### Input

{% highlight liquid %}
{% raw %}
{{ page.next.title }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
/2016/01/02/hello-world.html
{% endhighlight %}
