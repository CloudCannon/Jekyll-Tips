---
title: "push"
description: "Adds an object to a array."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
{% assign my_array = "a,b,c" | split:"," %}
{% assign my_array = my_array | push: 'd' %}

{{ my_array | array_to_sentence_string }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
a, b, c, and d
{% endhighlight %}