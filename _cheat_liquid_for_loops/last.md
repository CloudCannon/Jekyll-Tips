---
title: "last"
description: "Returns whether it's the last iteration."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is [1, 2, 3] -->
{% for item in page.my_array %}
  {% if forloop.last %}
    Last!
  {% else %}
    Not last
  {% endif %}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Not last Not last Last!
{% endhighlight %}
