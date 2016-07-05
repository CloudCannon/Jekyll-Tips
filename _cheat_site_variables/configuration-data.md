---
title: "*configuration data*"
description: "All the variables set via the command line and your `_config.yml` are available through `site`."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- url is set to http://mysite.com in the configuration file -->
{{ site.url }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
http://mysite.com
{% endhighlight %}
