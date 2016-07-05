---
title: "index"
description: "index of the current iteration."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.index }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
1 2 3
{% endhighlight %}
