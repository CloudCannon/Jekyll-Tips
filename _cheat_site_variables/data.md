---
title: "data"
description: "A list containing the data loaded from the YAML, JSON and CSV files located in the _data directory."
---
##### Input

{% highlight liquid %}
{% raw %}
{{ site.data.nba_players.first.name }}
{% endraw %}
{% endhighlight %}

##### Output

{% highlight html %}
Michael Jordan
{% endhighlight %}
