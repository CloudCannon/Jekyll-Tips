---
title: "categories"
description: "The list of categories to which this post belongs."
---
##### Input

{% highlight liquid %}
{% raw %}
<!-- tags is set to
  categories:
    - news
-->
{{ page.categories | array_to_sentence_string  }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
news
{% endhighlight %}
