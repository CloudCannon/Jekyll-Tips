---
title: "array_to_sentence_string"
description: "Append characters to a string."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | array_to_sentence_string }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
a, b, and c
{% endhighlight %}
