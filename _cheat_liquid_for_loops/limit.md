---
title: "limit"
description: "Restrict how many items are looped through."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is [1, 2, 3, 4, 5] -->
{% for item in page.my_array limit: 2 %}
  {{ item }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
1 2
{% endhighlight %}
