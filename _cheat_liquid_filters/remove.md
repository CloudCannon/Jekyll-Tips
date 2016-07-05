---
title: "remove"
description: "Removes any occurrence of a substring from a string."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ 'I really really like Jekyll' | remove: 'really' }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
I like Jekyll
{% endhighlight %}
