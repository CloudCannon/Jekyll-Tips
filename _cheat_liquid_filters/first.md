---
title: "first"
description: "Get the first element of the passed in array."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | first }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
a
{% endhighlight %}
