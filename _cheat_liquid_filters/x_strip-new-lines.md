---
description: "Removes all newlines from the input"
---
##### Input
{% highlight liquid %}
	{% raw %}
		{{ "Jekyll \n be" | strip_new_lines }}
	{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
	Jekyll is cool
{% endhighlight %}
