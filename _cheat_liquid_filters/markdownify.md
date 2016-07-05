---
title: "markdownify"
description: "Convert a Markdown-formatted string into HTML."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "Hello **Jekyll**" | markdownify }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Hello <strong>Jekyll</strong>
{% endhighlight %}
