---
title: "textilize"
description: "Convert a Textile-formatted string into HTML."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "h1. Hello Jekyll" | textilize }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
<h1>Hello Jekyll</h1>
{% endhighlight %}
