---
title: "index0"
description: "index of the current iteration (zero based)."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.index0 }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
0 1 2
{% endhighlight %}
