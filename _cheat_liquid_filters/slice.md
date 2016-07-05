---
title: "slice"
description: "returns a substring, starting at the specified index."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "hello" | slice: 0 }}
{{ "hello" | slice: 1 }}
{{ "hello" | slice: 1, 3 }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
h
e
ell
{% endhighlight %}
