---
title: "html_pages"
description: "A subset of `site.pages` listing those which end in `.html`"
---
##### Input

{% highlight liquid %}
{% raw %}
{% for p in site.html_pages %}
  {{ p.path }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
about.html
contact.html
index.html
{% endhighlight %}
