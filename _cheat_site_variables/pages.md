---
title: "pages"
description: "A list of all Pages."
---
##### Input

{% highlight liquid %}
{% raw %}
{% for p in site.pages %}
  {{ p.path }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
about.html
contact.html
index.html
site-map.xml
{% endhighlight %}
