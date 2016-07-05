---
title: "uri_escape"
description: "URI escape a string."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "foo, bar \baz?" | uri_escape }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
foo,%20bar%20%5Cbaz?
{% endhighlight %}
