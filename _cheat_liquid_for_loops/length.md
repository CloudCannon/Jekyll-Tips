---
title: "length"
description: "Length of the entire loop."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.length }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
3 3 3
{% endhighlight %}
