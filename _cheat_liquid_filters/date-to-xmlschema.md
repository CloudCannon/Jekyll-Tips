---
title: "date_to_xmlschema"
description: "Convert a Date into ISO 8601 format."
category: Date
---
##### Input
{% highlight liquid %}
{% raw %}
{{ site.time | date_to_xmlschema }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
2008-11-07T13:07:54-08:00
{% endhighlight %}
