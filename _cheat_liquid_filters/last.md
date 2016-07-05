---
title: "last"
description: "Get the last element of the passed in array."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | last }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
c
{% endhighlight %}
