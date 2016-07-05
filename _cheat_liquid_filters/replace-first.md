---
title: "replace_first"
description: "Replaces only the first occurrence of a substring from a string."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ 'I really really like Jekyll' | replace_first: 'really', 'kinda' }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
I kinda really like Jekyll
{% endhighlight %}
