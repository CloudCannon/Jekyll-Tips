---
title: "strip_html"
description: "Strip all html tags from the input string."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "<p>Jekyll is cool</p>" | strip_html }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Jekyll is cool
{% endhighlight %}
