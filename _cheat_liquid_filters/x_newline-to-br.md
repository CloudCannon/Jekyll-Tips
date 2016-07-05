---
description: "replace each newline (\n) with a <br>"
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- _/posts/2016-01-01-hello.md contains a multiple line string.  -->
{{ site.posts.first.content | newline_to_br }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
1
{% endhighlight %}
