---
title: "comment"
description: Don't output the contained text.
category: Other
---
##### Input

{% highlight liquid %}
{% raw %}
My name is {% comment %}Mr{% endcomment %} Jekyll
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
My name is Jekyll
{% endhighlight %}
