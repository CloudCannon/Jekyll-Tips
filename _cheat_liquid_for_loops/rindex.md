---
title: "rindex"
description: "Outputs the number of iterations left."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.rindex }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
3 2 1
{% endhighlight %}
