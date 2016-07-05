---
title: "cgi_escape"
description: "Escape a string for use in a URL."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "foo,bar;baz?" | cgi_escape }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
foo%2Cbar%3Bbaz%3F
{% endhighlight %}
