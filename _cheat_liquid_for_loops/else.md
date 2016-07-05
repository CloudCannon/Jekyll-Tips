---
title: "else"
description: "Condition when there are no items in the array."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.my_array is [] -->
{% for item in page.my_array %}
  {{ item }}
{% else %}
  There are no items!
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
There are no items!
{% endhighlight %}
