---
title: "cycle"
description: "Loops through a group of strings and outputs them in the order that they were passed as parameters."
category: Iteration
---

`cycle` must be used within a for loop block.

##### Input

{% highlight liquid %}
{% raw %}
{% for i in (1..5) %}
  {% cycle 'red', 'blue', 'yellow' %}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight liquid %}
red blue yellow red blue
{% endhighlight %}
