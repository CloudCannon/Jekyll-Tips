---
description: "Convert quotes into smart quotes."
---
##### Input
{% highlight liquid %}
{% raw %}
{{ "That's funny" | smartify }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
the-config-yml-file
{% endhighlight %}

The slugify filter accepts an option, each specifying what to filter. The default is default. They are as follows (with what they filter):

* `none`: no characters
* `raw`: spaces
* `default`: spaces and non-alphanumeric characters
* `pretty`: spaces and non-alphanumeric characters except for `._~!$&'()+,;=@`
