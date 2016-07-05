---
title: "offset"
description: "Start looping from the nth item."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is [1, 2, 3, 4, 5] -->
{% for item in page.my_array offset: 2 %}
  {{ item }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
3 4 5
{% endhighlight %}
