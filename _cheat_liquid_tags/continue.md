---
title: "continue"
description: "Causes the loop to skip the current iteration."
category: Iteration
---
##### Input
{% highlight liquid %}
{% raw %}
{% for i in (1..5) %}
  {% if i == 3 %}
    {% continue %}
  {% else %}
    {{ i }}
  {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output
{% highlight liquid %}
1 2 4 5
{% endhighlight %}
