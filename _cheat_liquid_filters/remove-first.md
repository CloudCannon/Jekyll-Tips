---
title: "remove_first"
description: "Removes only the first occurrence of a substring from a string."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ 'I really really like Jekyll' | remove_first: 'really' }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
I really like Jekyll
{% endhighlight %}
