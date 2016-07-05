---
title: "join"
description: "Joins an array with the specified character."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | join: ', ' }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
a, b, c
{% endhighlight %}
