---
title: "reversed"
description: "Reverses the order."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is [1, 2, 3, 4, 5] -->
{% for item in page.my_array reversed %}
  {{ item }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
5 4 3 2 1
{% endhighlight %}
