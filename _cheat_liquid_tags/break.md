---
title: "break"
description: "Causes the loop to stop iterating."
category: Iteration
---
##### Input
{% highlight liquid %}
{% raw %}
{% for i in (1..5) %}
  {% if i == 3 %}
    {% break %}
  {% else %}
    {{ i }}
  {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight liquid %}
1 2
{% endhighlight %}
