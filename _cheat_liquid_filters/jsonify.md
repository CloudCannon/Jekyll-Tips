---
title: "jsonify"
description: "Convert Hash or Array to JSON."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.my_array is ['a', 'b', 'c'] -->
{{ page.my_array | jsonify }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
["a","b","c"]
{% endhighlight %}
