---
title: "include"
description: "Inserts a file from the `_includes` directory."
category: Other
---
##### Input

{% highlight liquid %}
{% raw %}
<h1>My site</h1>
{% include nav.html %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
<h1>My Site</h1>
<ul class="nav">
  <li><a href="/">Home</a></li>
  <li><a href="/about/">About</a></li>
  <li><a href="/contact/">Contact</a></li>
</ul>
{% endhighlight %}
