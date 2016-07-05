---
title: "assign"
description: "Create a new variable."
category: Variable
---
##### Input

{% highlight liquid %}
{% raw %}
{% assign my_variable = false %}
{% if my_variable != true %}
  Hi there!
{% endif %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Hi there!
{% endhighlight %}
