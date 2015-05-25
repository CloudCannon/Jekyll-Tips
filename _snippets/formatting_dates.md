---
title: Formatting dates
category: Other
---

### Month, day, year
{% highlight liquid %}
{% raw %}
{{ page.date | date: "%B %-d, %Y" }}
{% endraw %}
{% endhighlight %}

### Current year
{% highlight liquid %}
{% raw %}
{{ site.time | date: '%Y' }}
{% endraw %}
{% endhighlight %}
