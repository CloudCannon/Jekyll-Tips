---
description: "A subset of `site.static_files` listing those which end in `.html`."
---
##### Input

{% highlight liquid %}
{% raw %}
{% for p in site.html_files %}
  {{ p.path }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
about.html contact.html index.html
{% endhighlight %}
