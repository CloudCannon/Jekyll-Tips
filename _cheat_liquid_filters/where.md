---
title: "where"
description: "Select all the objects in an array where the key has the given value."
category: Array
---
##### Input
{% highlight liquid %}
{% raw %}
<!-- page.people is
  - name: "John"
    school: "Stanford"
  - name: "Jane"
    school: "Stanford"
  - name: "Joe"
    school: "Harvard"
-->
{{ page.people | where: "school", "Stanford" }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
{"name"=>"John", "school"=>"Stanford"}{"name"=>"Jane", "school"=>"Stanford"}
{% endhighlight %}
