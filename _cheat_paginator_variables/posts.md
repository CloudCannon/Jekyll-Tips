---
title: "posts"
description: "A list of posts for the current page."
---
##### Input

{% highlight liquid %}
{% raw %}
{% for post in paginator.posts %}
  {{ post.id }}
{% endfor %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
/2016/01/03/no-im-not /2016/01/04/im-back /2016/01/03/goodbye-world /2016/01/02/im-fleeting
{% endhighlight %}
