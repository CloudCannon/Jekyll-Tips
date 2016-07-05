---
title: "rindex0"
description: "Outputs the number of iterations left (zero based)."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{% for item in page.my_array %}
  {{ forloop.rindex0 }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
2 1 0
{% endhighlight %}
