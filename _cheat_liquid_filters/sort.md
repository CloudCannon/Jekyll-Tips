---
title: "sort"
description: "Sorts an array."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['c', 'a', 'b'] -->
{{ page.my_array | sort }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
['a','b','c']
{% endhighlight %}
