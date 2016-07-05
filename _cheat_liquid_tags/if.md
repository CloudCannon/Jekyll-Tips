---
title: "if"
description: "Executes a block of code only if a certain condition is met."
category: Control Flow
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.name is set to "about" -->
{% if page.name == 'about' %}
  About Page
{% endif %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
  About Page
{% endhighlight %}
