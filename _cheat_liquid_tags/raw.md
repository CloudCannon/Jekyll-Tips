---
title: "raw"
description: No liquid will be parsed in within these tags.
category: Other
---
##### Input

{% highlight liquid %}
{% assign l_bracket = "{" %}
{% assign r_bracket = "}" %}
{% raw %}
{% raw %}
  {{ page.title }}{% endraw %}
{{ l_bracket}}% endraw %{{ r_bracket }}
{% endhighlight %}

##### Output
{% highlight html %}
{% raw %}
{{ page.title }}
{% endraw %}
{% endhighlight %}
