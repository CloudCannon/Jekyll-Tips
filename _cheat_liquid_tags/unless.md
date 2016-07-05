---
title: "unless"
description: "Similar to `if`, but executes a block of code only if a certain condition is **not** met."
category: Control Flow
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- page.name is set to "about" -->
{% unless page.name == "contact" %}
  It's not the contact page
{% endunless %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
It's not the contact page
{% endhighlight %}

Which is the same as doing:

{% highlight liquid %}
{% raw %}
{% if page.name != "contact" %}
  It's not the contact page
{% endif %}
{% endraw %}
{% endhighlight %}
