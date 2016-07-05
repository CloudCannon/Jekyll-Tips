---
title: "for"
description: "Repeatedly executes a block of code."
category: Iteration
---
##### Input

{% highlight liquid %}
{% raw %}
{% for page in site.pages %}
  {{ page.title }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
index
about
contact
{% endhighlight %}
