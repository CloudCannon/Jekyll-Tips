---
title: "replace"
description: "Replaces any occurrence of a substring from a string."
category: String
---
##### Input
{% highlight liquid %}
{% raw %}
{{ 'I really really like Jekyll' | replace: 'really', 'truly' }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
I truly truly like Jekyll
{% endhighlight %}
