---
title: "elsif"
description: "Adds more conditions to an `if` or `unless` block."
category: Control Flow
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.name is set to "contact" -->
{% if page.name == 'about' %}
  About Page
{% elsif page.name == 'contact' %}
  Contact Page
{% else %}
  Other Page
{% endif %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Contact Page
{% endhighlight %}
