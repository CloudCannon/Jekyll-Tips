---
title: "tags"
description: "The list of tags to which this post belongs."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- tags is set to
  tags:
    - HTML
    - CSS
-->
{{ page.tags | array_to_sentence_string  }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
HTML and CSS
{% endhighlight %}
