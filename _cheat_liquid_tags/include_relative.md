---
title: "include_relative"
description: "Includes a file relative to the current file."
category: Other
---
##### Input

{% highlight liquid %}
{% raw %}
<h1>My site</h1>
{% include_relative about.html %}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
<h1>My Site</h1>
<h1>About</h1>
{% endhighlight %}
